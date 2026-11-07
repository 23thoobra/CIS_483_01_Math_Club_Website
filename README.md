CIS 483/583 - Homework 3: CSS - Styling
Author: Braden Thooft
GitHub: https://github.com/23thoobra/CIS-4833-01---Assignment_2_Math_club

While testing the registration form, I noticed that the input borders never changed color when I hovered over them, and an empty required field did not get its red dashed border after I pressed Register. I right-clicked the Email field, chose Inspect, and in the DevTools Styles pane my "input:hover" and "input:user-invalid" border rules were crossed out. The rule winning above them was my shared field rule, input:not([type="radio"]):not([type="checkbox"]), which I wrote to style every text box but skip the radio buttons and checkboxes. Each :not() counts the attribute selector inside it, so that rule's specificity was (0,2,1) and beat the (0,1,1) of input:hover even though the hover rule came later in the file. I fixed this formatting error by wrapping the shared selector in :where(), which gives it zero specificity, so the hover, focus, and invalid rules now win the cascade by source order. After the change, the Styles pane showed the shared rule's border-color crossed out instead, and hovering, focusing, and invalid fields all displayed correctly.

Sources:
- MDN Web Docs, CSS reference: https://developer.mozilla.org/en-US/docs/Web/CSS
- MDN, Specificity: https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity
- MDN, :where(): https://developer.mozilla.org/en-US/docs/Web/CSS/:where
- MDN, :user-invalid: https://developer.mozilla.org/en-US/docs/Web/CSS/:user-invalid
- MDN, Basic concepts of flexbox: https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_flexible_box_layout/Basic_concepts_of_flexbox
- WebAIM Contrast Checker: https://webaim.org/resources/contrastchecker/