---
title: Bir Windows Formundaki Denetimler için Erişilebilirlik Bilgileri Sağlama
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, accessibility
- controls [Windows Forms], accessibility
- accessibility [Windows Forms], Windows Forms controls
ms.assetid: 887dee6f-5059-4d57-957d-7c6fcd4acb10
ms.openlocfilehash: 0f589f37d79c9ec8d55153aac4c846726a379055
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59218335"
---
# <a name="providing-accessibility-information-for-controls-on-a-windows-form"></a><span data-ttu-id="d74b4-102">Bir Windows Formundaki Denetimler için Erişilebilirlik Bilgileri Sağlama</span><span class="sxs-lookup"><span data-stu-id="d74b4-102">Providing Accessibility Information for Controls on a Windows Form</span></span>
<span data-ttu-id="d74b4-103">Erişilebilirlik yardımları özel programları ve engelli kişilerin yardımcı aygıtları bilgisayarlar daha etkili bir şekilde kullanır.</span><span class="sxs-lookup"><span data-stu-id="d74b4-103">Accessibility aids are specialized programs and devices that help people with disabilities use computers more effectively.</span></span> <span data-ttu-id="d74b4-104">Ekran okuyucuları, klavye ve fare kullanmak yerine sözlü komutları sağlayan kişiler için gizli ve ses giriş yardımcı olan kişilere yönelik olarak verilebilir.</span><span class="sxs-lookup"><span data-stu-id="d74b4-104">Examples include screen readers for people who are blind and voice input utilities for people who provide verbal commands instead of using the mouse or keyboard.</span></span> <span data-ttu-id="d74b4-105">Bu erişilebilirlik yardımları Windows Forms denetimleri tarafından kullanıma sunulan erişilebilirlik özellikleri ile etkileşim kurun.</span><span class="sxs-lookup"><span data-stu-id="d74b4-105">These accessibility aids interact with the accessibility properties exposed by Windows Forms controls.</span></span> <span data-ttu-id="d74b4-106">Bu özellikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d74b4-106">These properties are:</span></span>  
  
-   <span data-ttu-id="d74b4-107">**AccessibilityObject**</span><span class="sxs-lookup"><span data-stu-id="d74b4-107">**AccessibilityObject**</span></span>  
  
-   <span data-ttu-id="d74b4-108">**AccessibleDefaultActionDescription**</span><span class="sxs-lookup"><span data-stu-id="d74b4-108">**AccessibleDefaultActionDescription**</span></span>  
  
-   <span data-ttu-id="d74b4-109">**AccessibleDescription**</span><span class="sxs-lookup"><span data-stu-id="d74b4-109">**AccessibleDescription**</span></span>  
  
-   <span data-ttu-id="d74b4-110">**AccessibleName**</span><span class="sxs-lookup"><span data-stu-id="d74b4-110">**AccessibleName**</span></span>  
  
-   <span data-ttu-id="d74b4-111">**AccessibleRole**</span><span class="sxs-lookup"><span data-stu-id="d74b4-111">**AccessibleRole**</span></span>  
  
## <a name="accessibilityobject-property"></a><span data-ttu-id="d74b4-112">AccessibilityObject özelliği</span><span class="sxs-lookup"><span data-stu-id="d74b4-112">AccessibilityObject Property</span></span>  
 <span data-ttu-id="d74b4-113">Bu salt okunur özelliği içeren bir <xref:System.Windows.Forms.AccessibleObject> örneği.</span><span class="sxs-lookup"><span data-stu-id="d74b4-113">This read-only property contains an <xref:System.Windows.Forms.AccessibleObject> instance.</span></span> <span data-ttu-id="d74b4-114">**AccessibleObject** uygulayan <xref:Accessibility.IAccessible> denetimin açıklaması, ekran konumunu, gezinme yeteneklerini ve değeri hakkında bilgi sağlayan bir arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d74b4-114">The **AccessibleObject** implements the <xref:Accessibility.IAccessible> interface, which provides information about the control's description, screen location, navigational abilities, and value.</span></span> <span data-ttu-id="d74b4-115">Tasarımcı, denetimi forma eklendiğinde bu değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d74b4-115">The designer sets this value when the control is added to the form.</span></span>  
  
## <a name="accessibledefaultactiondescription-property"></a><span data-ttu-id="d74b4-116">AccessibleDefaultActionDescription özelliği</span><span class="sxs-lookup"><span data-stu-id="d74b4-116">AccessibleDefaultActionDescription Property</span></span>  
 <span data-ttu-id="d74b4-117">Bu dize, denetimin eylemi açıklar.</span><span class="sxs-lookup"><span data-stu-id="d74b4-117">This string describes the action of the control.</span></span> <span data-ttu-id="d74b4-118">Özellikler penceresinde görünmez ve yalnızca kodda ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="d74b4-118">It does not appear in the Properties window and may only be set in code.</span></span> <span data-ttu-id="d74b4-119">Aşağıdaki örnekte, bu özellik bir düğme denetimi için ayarlar:</span><span class="sxs-lookup"><span data-stu-id="d74b4-119">The following example sets this property for a button control:</span></span>  
  
```  
' Visual Basic  
Button1.AccessibleDefaultActionDescription = _  
   "Closes the application."  
  
// C#  
Button1.AccessibleDefaultActionDescription =   
   "Closes the application.";  
  
// C++  
button1->AccessibleDefaultActionDescription =  
   "Closes the application.";  
```  
  
## <a name="accessibledescription-property"></a><span data-ttu-id="d74b4-120">AccessibleDescription özelliği</span><span class="sxs-lookup"><span data-stu-id="d74b4-120">AccessibleDescription Property</span></span>  
 <span data-ttu-id="d74b4-121">Bu dize bir denetimi açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="d74b4-121">This string describes the control.</span></span> <span data-ttu-id="d74b4-122">Bu Özellikler penceresinde veya kod aşağıdaki gibi ayarlanabilir:</span><span class="sxs-lookup"><span data-stu-id="d74b4-122">It may be set in the Properties window, or in code as follows:</span></span>  
  
```  
' Visual Basic  
Button1.AccessibleDescription = "A button with text 'Exit'."  
  
// C#  
Button1.AccessibleDescription = "A button with text 'Exit'";  
  
// C++  
button1->AccessibleDescription = "A button with text 'Exit'";  
```  
  
## <a name="accessiblename-property"></a><span data-ttu-id="d74b4-123">AccessibleName özelliği</span><span class="sxs-lookup"><span data-stu-id="d74b4-123">AccessibleName Property</span></span>  
 <span data-ttu-id="d74b4-124">Erişilebilirlik yardımları bildirilen bir denetimin adıdır.</span><span class="sxs-lookup"><span data-stu-id="d74b4-124">This is the name of a control reported to accessibility aids.</span></span> <span data-ttu-id="d74b4-125">Bu Özellikler penceresinde veya kod aşağıdaki gibi ayarlanabilir:</span><span class="sxs-lookup"><span data-stu-id="d74b4-125">It may be set in the Properties window, or in code as follows:</span></span>  
  
```  
' Visual Basic  
Button1.AccessibleName = "Order"  
  
// C#  
Button1.AccessibleName = "Order";  
  
// C++  
button1->AccessibleName = "Order";  
```  
  
## <a name="accessiblerole-property"></a><span data-ttu-id="d74b4-126">AccessibleRole özelliği</span><span class="sxs-lookup"><span data-stu-id="d74b4-126">AccessibleRole Property</span></span>  
 <span data-ttu-id="d74b4-127">Bu özellik içeren bir <xref:System.Windows.Forms.AccessibleRole> numaralandırma denetim kullanıcı arabirimi rolünü açıklar.</span><span class="sxs-lookup"><span data-stu-id="d74b4-127">This property, which contains an <xref:System.Windows.Forms.AccessibleRole> enumeration, describes the user interface role of the control.</span></span> <span data-ttu-id="d74b4-128">Yeni bir denetim ayarlanmış değere sahip `Default`.</span><span class="sxs-lookup"><span data-stu-id="d74b4-128">A new control has the value set to `Default`.</span></span> <span data-ttu-id="d74b4-129">Bu, varsayılan olarak, açardı bir **düğmesi** denetim görür bir **düğmesi**.</span><span class="sxs-lookup"><span data-stu-id="d74b4-129">This would mean that by default, a **Button** control acts as a **Button**.</span></span> <span data-ttu-id="d74b4-130">Bir denetimi başka bir rol varsa bu özelliği sıfırlamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d74b4-130">You may want to reset this property if a control has another role.</span></span> <span data-ttu-id="d74b4-131">Örneğin, kullanmakta olduğunuz bir **PictureBox** olarak denetim bir **grafik**, ve rol olarak bildirmek için erişilebilirlik yardımları isteyebileceğiniz bir **grafik**, olarak değil bir **PictureBox** .</span><span class="sxs-lookup"><span data-stu-id="d74b4-131">For example, you may be using a **PictureBox** control as a **Chart**, and you may want accessibility aids to report the role as a **Chart**, not as a **PictureBox**.</span></span> <span data-ttu-id="d74b4-132">Bu özellik, geliştirdiğiniz özel denetimler için belirtmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d74b4-132">You may also want to specify this property for custom controls you have developed.</span></span> <span data-ttu-id="d74b4-133">Bu özellik Özellikler penceresinde veya kod aşağıdaki gibi ayarlanabilir:</span><span class="sxs-lookup"><span data-stu-id="d74b4-133">This property may be set in the Properties window, or in code as follows:</span></span>  
  
```  
' Visual Basic  
PictureBox1.AccessibleRole = AccessibleRole.Chart  
  
// C#  
PictureBox1.AccessibleRole = AccessibleRole.Chart;  
  
// C++  
pictureBox1->AccessibleRole = AccessibleRole::Chart;  
```  
  
## <a name="see-also"></a><span data-ttu-id="d74b4-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d74b4-134">See also</span></span>

- <xref:System.Windows.Forms.AccessibleObject>
- <xref:System.Windows.Forms.Control.AccessibilityObject%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleDefaultActionDescription%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleDescription%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleName%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleRole%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.AccessibleRole>
