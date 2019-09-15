---
title: Bir Windows Formundaki Denetimler için Erişilebilirlik Bilgileri Sağlama
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, accessibility
- controls [Windows Forms], accessibility
- accessibility [Windows Forms], Windows Forms controls
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 887dee6f-5059-4d57-957d-7c6fcd4acb10
ms.openlocfilehash: 791944bd9e8f5520a571e6fb415d69022aa0bead
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991709"
---
# <a name="providing-accessibility-information-for-controls-on-a-windows-form"></a><span data-ttu-id="8b913-102">Bir Windows Formundaki Denetimler için Erişilebilirlik Bilgileri Sağlama</span><span class="sxs-lookup"><span data-stu-id="8b913-102">Providing Accessibility Information for Controls on a Windows Form</span></span>
<span data-ttu-id="8b913-103">Erişilebilirlik yardımları, Engelli kişilerin bilgisayarları daha verimli bir şekilde kullanmasına yardımcı olan özel programlar ve cihazlardır.</span><span class="sxs-lookup"><span data-stu-id="8b913-103">Accessibility aids are specialized programs and devices that help people with disabilities use computers more effectively.</span></span> <span data-ttu-id="8b913-104">Bu örneklerde, fare veya klavyeyi kullanmak yerine, kısayol tuşları sağlayan kişiler için görme ve ses girişi yardımcı programları için ekran okuyucular bulunur.</span><span class="sxs-lookup"><span data-stu-id="8b913-104">Examples include screen readers for people who are blind and voice input utilities for people who provide verbal commands instead of using the mouse or keyboard.</span></span> <span data-ttu-id="8b913-105">Bu erişilebilirlik yardımları, Windows Forms denetimleri tarafından sunulan erişilebilirlik özellikleriyle etkileşime geçebilir.</span><span class="sxs-lookup"><span data-stu-id="8b913-105">These accessibility aids interact with the accessibility properties exposed by Windows Forms controls.</span></span> <span data-ttu-id="8b913-106">Bu özellikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8b913-106">These properties are:</span></span>  
  
- <span data-ttu-id="8b913-107">**AccessibilityObject**</span><span class="sxs-lookup"><span data-stu-id="8b913-107">**AccessibilityObject**</span></span>  
  
- <span data-ttu-id="8b913-108">**Erişilebilir Defaultactiondescription**</span><span class="sxs-lookup"><span data-stu-id="8b913-108">**AccessibleDefaultActionDescription**</span></span>  
  
- <span data-ttu-id="8b913-109">**Erişilebilir açıklama**</span><span class="sxs-lookup"><span data-stu-id="8b913-109">**AccessibleDescription**</span></span>  
  
- <span data-ttu-id="8b913-110">**Erişilebilir ad**</span><span class="sxs-lookup"><span data-stu-id="8b913-110">**AccessibleName**</span></span>  
  
- <span data-ttu-id="8b913-111">**Erişilebilir OLE**</span><span class="sxs-lookup"><span data-stu-id="8b913-111">**AccessibleRole**</span></span>  
  
## <a name="accessibilityobject-property"></a><span data-ttu-id="8b913-112">AccessibilityObject özelliği</span><span class="sxs-lookup"><span data-stu-id="8b913-112">AccessibilityObject Property</span></span>  
 <span data-ttu-id="8b913-113">Bu salt okunurdur özelliği bir <xref:System.Windows.Forms.AccessibleObject> örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="8b913-113">This read-only property contains an <xref:System.Windows.Forms.AccessibleObject> instance.</span></span> <span data-ttu-id="8b913-114">**Erişilebilir nesne** , denetimin açıklaması, <xref:Accessibility.IAccessible> ekran konumu, gezinme becerileri ve değer hakkında bilgi sağlayan arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="8b913-114">The **AccessibleObject** implements the <xref:Accessibility.IAccessible> interface, which provides information about the control's description, screen location, navigational abilities, and value.</span></span> <span data-ttu-id="8b913-115">Tasarımcı, bu değeri denetim forma eklendiğinde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8b913-115">The designer sets this value when the control is added to the form.</span></span>  
  
## <a name="accessibledefaultactiondescription-property"></a><span data-ttu-id="8b913-116">Erişilebilir Defaultactiondescription özelliği</span><span class="sxs-lookup"><span data-stu-id="8b913-116">AccessibleDefaultActionDescription Property</span></span>  
 <span data-ttu-id="8b913-117">Bu dize, denetimin eylemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b913-117">This string describes the action of the control.</span></span> <span data-ttu-id="8b913-118">Özellikler penceresi görünmez ve yalnızca kodda ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="8b913-118">It does not appear in the Properties window and may only be set in code.</span></span> <span data-ttu-id="8b913-119">Aşağıdaki örnek, bir düğme denetimi için bu özelliği ayarlar:</span><span class="sxs-lookup"><span data-stu-id="8b913-119">The following example sets this property for a button control:</span></span>  
  
```vb  
Button1.AccessibleDefaultActionDescription = _  
   "Closes the application."  
``` 

```csharp  
Button1.AccessibleDefaultActionDescription =   
   "Closes the application.";  
```

```cpp  
button1->AccessibleDefaultActionDescription =  
   "Closes the application.";  
```  
  
## <a name="accessibledescription-property"></a><span data-ttu-id="8b913-120">Erişilebilir Açıklama özelliği</span><span class="sxs-lookup"><span data-stu-id="8b913-120">AccessibleDescription Property</span></span>  
 <span data-ttu-id="8b913-121">Bu dize, denetimi açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b913-121">This string describes the control.</span></span> <span data-ttu-id="8b913-122">Özellikler penceresi veya kodda aşağıdaki gibi ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="8b913-122">It may be set in the Properties window, or in code as follows:</span></span>  
  
```vb  
Button1.AccessibleDescription = "A button with text 'Exit'."  
```

```csharp  
Button1.AccessibleDescription = "A button with text 'Exit'";  
```

```cpp  
button1->AccessibleDescription = "A button with text 'Exit'";  
```  
  
## <a name="accessiblename-property"></a><span data-ttu-id="8b913-123">Erişilebilirblename özelliği</span><span class="sxs-lookup"><span data-stu-id="8b913-123">AccessibleName Property</span></span>  
 <span data-ttu-id="8b913-124">Bu, erişilebilirlik yardımlarına bildirilen bir denetimin adıdır.</span><span class="sxs-lookup"><span data-stu-id="8b913-124">This is the name of a control reported to accessibility aids.</span></span> <span data-ttu-id="8b913-125">Özellikler penceresi veya kodda aşağıdaki gibi ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="8b913-125">It may be set in the Properties window, or in code as follows:</span></span>  
  
```vb  
Button1.AccessibleName = "Order"  
```

```csharp  
Button1.AccessibleName = "Order";  
```

```cpp  
button1->AccessibleName = "Order";  
```  
  
## <a name="accessiblerole-property"></a><span data-ttu-id="8b913-126">Erişilebilir OLE özelliği</span><span class="sxs-lookup"><span data-stu-id="8b913-126">AccessibleRole Property</span></span>  
 <span data-ttu-id="8b913-127">Bir <xref:System.Windows.Forms.AccessibleRole> sabit listesi içeren bu özellik, denetimin kullanıcı arabirimi rolünü açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b913-127">This property, which contains an <xref:System.Windows.Forms.AccessibleRole> enumeration, describes the user interface role of the control.</span></span> <span data-ttu-id="8b913-128">Yeni bir denetimin değeri olarak `Default`ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="8b913-128">A new control has the value set to `Default`.</span></span> <span data-ttu-id="8b913-129">Bu, varsayılan olarak bir **düğme** denetiminin **düğme**işlevi gördüğü anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8b913-129">This would mean that by default, a **Button** control acts as a **Button**.</span></span> <span data-ttu-id="8b913-130">Bir denetimin başka bir rolü varsa, bu özelliği sıfırlamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b913-130">You may want to reset this property if a control has another role.</span></span> <span data-ttu-id="8b913-131">Örneğin, bir **PictureBox** denetimini **grafik**olarak kullanıyor olabilirsiniz ve erişilebilirlik yardımlarının rolü **PictureBox**olarak değil bir **grafik**olarak rapor etmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b913-131">For example, you may be using a **PictureBox** control as a **Chart**, and you may want accessibility aids to report the role as a **Chart**, not as a **PictureBox**.</span></span> <span data-ttu-id="8b913-132">Bu özelliği, geliştirmiş olduğunuz özel denetimler için de belirtmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b913-132">You may also want to specify this property for custom controls you have developed.</span></span> <span data-ttu-id="8b913-133">Bu özellik Özellikler penceresi veya kodda aşağıdaki gibi ayarlanabilir:</span><span class="sxs-lookup"><span data-stu-id="8b913-133">This property may be set in the Properties window, or in code as follows:</span></span>  
  
```vb 
PictureBox1.AccessibleRole = AccessibleRole.Chart  
```

```csharp  
PictureBox1.AccessibleRole = AccessibleRole.Chart;  
```

```cpp  
pictureBox1->AccessibleRole = AccessibleRole::Chart;  
```  
  
## <a name="see-also"></a><span data-ttu-id="8b913-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b913-134">See also</span></span>

- <xref:System.Windows.Forms.AccessibleObject>
- <xref:System.Windows.Forms.Control.AccessibilityObject%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleDefaultActionDescription%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleDescription%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleName%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleRole%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.AccessibleRole>
