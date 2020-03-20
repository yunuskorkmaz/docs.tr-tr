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
ms.openlocfilehash: 672104db94826cfbe113a7ae0ea29546b0c3b9da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181996"
---
# <a name="providing-accessibility-information-for-controls-on-a-windows-form"></a><span data-ttu-id="2b5a0-102">Bir Windows Formundaki Denetimler için Erişilebilirlik Bilgileri Sağlama</span><span class="sxs-lookup"><span data-stu-id="2b5a0-102">Providing Accessibility Information for Controls on a Windows Form</span></span>
<span data-ttu-id="2b5a0-103">Erişilebilirlik yardımcıları, engelli kişilerin bilgisayarları daha etkili kullanmasına yardımcı olan özel programlar ve aygıtlardır.</span><span class="sxs-lookup"><span data-stu-id="2b5a0-103">Accessibility aids are specialized programs and devices that help people with disabilities use computers more effectively.</span></span> <span data-ttu-id="2b5a0-104">Örnekler arasında, fare veya klavye kullanmak yerine sözlü komutlar sağlayan kişiler için kör olan kişiler için ekran okuyucular ve ses girişi yardımcı programları yer alır.</span><span class="sxs-lookup"><span data-stu-id="2b5a0-104">Examples include screen readers for people who are blind and voice input utilities for people who provide verbal commands instead of using the mouse or keyboard.</span></span> <span data-ttu-id="2b5a0-105">Bu erişilebilirlik yardımcıları, Windows Forms denetimleri tarafından açığa çıkarılan erişilebilirlik özellikleriyle etkileşime girerek etkileşime girebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b5a0-105">These accessibility aids interact with the accessibility properties exposed by Windows Forms controls.</span></span> <span data-ttu-id="2b5a0-106">Bu özellikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="2b5a0-106">These properties are:</span></span>  
  
- <span data-ttu-id="2b5a0-107">**Accessibilityobject**</span><span class="sxs-lookup"><span data-stu-id="2b5a0-107">**AccessibilityObject**</span></span>  
  
- <span data-ttu-id="2b5a0-108">**ErişilebilirDefaultActionDescription**</span><span class="sxs-lookup"><span data-stu-id="2b5a0-108">**AccessibleDefaultActionDescription**</span></span>  
  
- <span data-ttu-id="2b5a0-109">**Accessibledescription**</span><span class="sxs-lookup"><span data-stu-id="2b5a0-109">**AccessibleDescription**</span></span>  
  
- <span data-ttu-id="2b5a0-110">**Accessiblename**</span><span class="sxs-lookup"><span data-stu-id="2b5a0-110">**AccessibleName**</span></span>  
  
- <span data-ttu-id="2b5a0-111">**Accessiblerole**</span><span class="sxs-lookup"><span data-stu-id="2b5a0-111">**AccessibleRole**</span></span>  
  
## <a name="accessibilityobject-property"></a><span data-ttu-id="2b5a0-112">ErişilebilirlikNesne Özelliği</span><span class="sxs-lookup"><span data-stu-id="2b5a0-112">AccessibilityObject Property</span></span>  
 <span data-ttu-id="2b5a0-113">Salt okunur özelliği bir <xref:System.Windows.Forms.AccessibleObject> örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="2b5a0-113">This read-only property contains an <xref:System.Windows.Forms.AccessibleObject> instance.</span></span> <span data-ttu-id="2b5a0-114">**Erişilebilir Nesne,** denetimin <xref:Accessibility.IAccessible> açıklaması, ekran konumu, gezinme yetenekleri ve değeri hakkında bilgi sağlayan arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="2b5a0-114">The **AccessibleObject** implements the <xref:Accessibility.IAccessible> interface, which provides information about the control's description, screen location, navigational abilities, and value.</span></span> <span data-ttu-id="2b5a0-115">Denetim forma eklendiğinde tasarımcı bu değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2b5a0-115">The designer sets this value when the control is added to the form.</span></span>  
  
## <a name="accessibledefaultactiondescription-property"></a><span data-ttu-id="2b5a0-116">ErişilebilirDefaultActionDescription Özelliği</span><span class="sxs-lookup"><span data-stu-id="2b5a0-116">AccessibleDefaultActionDescription Property</span></span>  
 <span data-ttu-id="2b5a0-117">Bu dize, denetimin eylemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="2b5a0-117">This string describes the action of the control.</span></span> <span data-ttu-id="2b5a0-118">Özellikler penceresinde görünmez ve yalnızca kod olarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="2b5a0-118">It does not appear in the Properties window and may only be set in code.</span></span> <span data-ttu-id="2b5a0-119">Aşağıdaki örnek, bir düğme denetimi için bu özelliği ayarlar:</span><span class="sxs-lookup"><span data-stu-id="2b5a0-119">The following example sets this property for a button control:</span></span>  
  
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
  
## <a name="accessibledescription-property"></a><span data-ttu-id="2b5a0-120">Erişilebilir Açıklama Özelliği</span><span class="sxs-lookup"><span data-stu-id="2b5a0-120">AccessibleDescription Property</span></span>  
 <span data-ttu-id="2b5a0-121">Bu dize denetimi açıklar.</span><span class="sxs-lookup"><span data-stu-id="2b5a0-121">This string describes the control.</span></span> <span data-ttu-id="2b5a0-122">Özellikler penceresinde veya kod olarak aşağıdaki gibi ayarlanabilir:</span><span class="sxs-lookup"><span data-stu-id="2b5a0-122">It may be set in the Properties window, or in code as follows:</span></span>  
  
```vb  
Button1.AccessibleDescription = "A button with text 'Exit'."  
```

```csharp  
Button1.AccessibleDescription = "A button with text 'Exit'";  
```

```cpp  
button1->AccessibleDescription = "A button with text 'Exit'";  
```  
  
## <a name="accessiblename-property"></a><span data-ttu-id="2b5a0-123">ErişilebilirAd Özelliği</span><span class="sxs-lookup"><span data-stu-id="2b5a0-123">AccessibleName Property</span></span>  
 <span data-ttu-id="2b5a0-124">Bu, erişilebilirlik yardımcılarına bildirilen bir denetimin adıdır.</span><span class="sxs-lookup"><span data-stu-id="2b5a0-124">This is the name of a control reported to accessibility aids.</span></span> <span data-ttu-id="2b5a0-125">Özellikler penceresinde veya kod olarak aşağıdaki gibi ayarlanabilir:</span><span class="sxs-lookup"><span data-stu-id="2b5a0-125">It may be set in the Properties window, or in code as follows:</span></span>  
  
```vb  
Button1.AccessibleName = "Order"  
```

```csharp  
Button1.AccessibleName = "Order";  
```

```cpp  
button1->AccessibleName = "Order";  
```  
  
## <a name="accessiblerole-property"></a><span data-ttu-id="2b5a0-126">ErişilebilirRol Özelliği</span><span class="sxs-lookup"><span data-stu-id="2b5a0-126">AccessibleRole Property</span></span>  
 <span data-ttu-id="2b5a0-127">Numaralandırma <xref:System.Windows.Forms.AccessibleRole> içeren bu özellik, denetimin kullanıcı arabirimi rolünü açıklar.</span><span class="sxs-lookup"><span data-stu-id="2b5a0-127">This property, which contains an <xref:System.Windows.Forms.AccessibleRole> enumeration, describes the user interface role of the control.</span></span> <span data-ttu-id="2b5a0-128">Yeni bir denetim değeri `Default`' ne göre ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="2b5a0-128">A new control has the value set to `Default`.</span></span> <span data-ttu-id="2b5a0-129">Bu, varsayılan olarak, bir **Düğme** denetiminin **Düğme**gibi hareket ettiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2b5a0-129">This would mean that by default, a **Button** control acts as a **Button**.</span></span> <span data-ttu-id="2b5a0-130">Denetimin başka bir rolü varsa bu özelliği sıfırlamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b5a0-130">You may want to reset this property if a control has another role.</span></span> <span data-ttu-id="2b5a0-131">Örneğin, **Bir Grafik**olarak **PictureBox** denetimi kullanıyor olabilirsiniz ve erişilebilirlik yardımcılarını, **Rolü PictureBox**olarak değil, **Grafik**olarak bildirmek için isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b5a0-131">For example, you may be using a **PictureBox** control as a **Chart**, and you may want accessibility aids to report the role as a **Chart**, not as a **PictureBox**.</span></span> <span data-ttu-id="2b5a0-132">Ayrıca, geliştirdiğiniz özel denetimler için bu özelliği belirtmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b5a0-132">You may also want to specify this property for custom controls you have developed.</span></span> <span data-ttu-id="2b5a0-133">Bu özellik Özellikler penceresinde veya kod olarak aşağıdaki gibi ayarlanabilir:</span><span class="sxs-lookup"><span data-stu-id="2b5a0-133">This property may be set in the Properties window, or in code as follows:</span></span>  
  
```vb
PictureBox1.AccessibleRole = AccessibleRole.Chart  
```

```csharp  
PictureBox1.AccessibleRole = AccessibleRole.Chart;  
```

```cpp  
pictureBox1->AccessibleRole = AccessibleRole::Chart;  
```  
  
## <a name="see-also"></a><span data-ttu-id="2b5a0-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b5a0-134">See also</span></span>

- <xref:System.Windows.Forms.AccessibleObject>
- <xref:System.Windows.Forms.Control.AccessibilityObject%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleDefaultActionDescription%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleDescription%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleName%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleRole%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.AccessibleRole>
