---
title: Windows Forms Denetimlerinde Özellik Tanımlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [Windows Forms], defining in code
- custom controls [Windows Forms], defining properties in code
ms.assetid: c2eb8277-a842-4d99-89a9-647b901a0434
ms.openlocfilehash: dc47d7152419d55b3e52aec70257e2b39e9aaca0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528329"
---
# <a name="defining-a-property-in-windows-forms-controls"></a><span data-ttu-id="32a5c-102">Windows Forms Denetimlerinde Özellik Tanımlama</span><span class="sxs-lookup"><span data-stu-id="32a5c-102">Defining a Property in Windows Forms Controls</span></span>
<span data-ttu-id="32a5c-103">Özellikler genel bakış için bkz: [özelliklerine genel bakış](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).</span><span class="sxs-lookup"><span data-stu-id="32a5c-103">For an overview of properties, see [Properties Overview](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).</span></span> <span data-ttu-id="32a5c-104">Bir özellik tanımlarken birkaç önemli noktalar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="32a5c-104">There are a few important considerations when defining a property:</span></span>  
  
-   <span data-ttu-id="32a5c-105">Tanımladığınız özellikleri öznitelikleri uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="32a5c-105">You must apply attributes to the properties you define.</span></span> <span data-ttu-id="32a5c-106">Tasarımcı bir özelliğin nasıl görüntülenmelidir öznitelikleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="32a5c-106">Attributes specify how the designer should display a property.</span></span> <span data-ttu-id="32a5c-107">Ayrıntılar için bkz [bileşenleri için tasarım zamanı öznitelikleri](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3).</span><span class="sxs-lookup"><span data-stu-id="32a5c-107">For details, see [Design-Time Attributes for Components](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3).</span></span>  
  
-   <span data-ttu-id="32a5c-108">Özellik değiştirme denetiminin görünümünü etkiliyorsa, çağrı <xref:System.Windows.Forms.Control.Invalidate%2A> yöntemi (denetiminizi devralan <xref:System.Windows.Forms.Control>) gelen `set` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="32a5c-108">If changing the property affects the visual display of the control, call the <xref:System.Windows.Forms.Control.Invalidate%2A> method (that your control inherits from <xref:System.Windows.Forms.Control>) from the `set` accessor.</span></span> <span data-ttu-id="32a5c-109"><xref:System.Windows.Forms.Control.Invalidate%2A> sırayla çağırır <xref:System.Windows.Forms.Control.OnPaint%2A> denetimi yeniden çizer yöntemi.</span><span class="sxs-lookup"><span data-stu-id="32a5c-109"><xref:System.Windows.Forms.Control.Invalidate%2A> in turn calls the <xref:System.Windows.Forms.Control.OnPaint%2A> method, which redraws the control.</span></span> <span data-ttu-id="32a5c-110">Birden çok çağrılar <xref:System.Windows.Forms.Control.Invalidate%2A> tek bir çağrı sonucunu <xref:System.Windows.Forms.Control.OnPaint%2A> verimlilik.</span><span class="sxs-lookup"><span data-stu-id="32a5c-110">Multiple calls to <xref:System.Windows.Forms.Control.Invalidate%2A> result in a single call to <xref:System.Windows.Forms.Control.OnPaint%2A> for efficiency.</span></span>  
  
-   <span data-ttu-id="32a5c-111">.NET Framework sınıf kitaplığı, tamsayı, ondalık sayılar, Boole değerleri ve diğerleri gibi ortak veri türleri için tür dönüştürücüleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="32a5c-111">The .NET Framework class library provides type converters for common data types such as integers, decimal numbers, Boolean values, and others.</span></span> <span data-ttu-id="32a5c-112">Genellikle amacı tür dönüştürücüsü, dize değeri bir dönüştürme (dize verilerini diğer veri türleri için) sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="32a5c-112">The purpose of a type converter is generally to provide string-to-value conversion (from string data to other data types).</span></span> <span data-ttu-id="32a5c-113">Ortak veri türleri değerleri dizeler ve uygun veri türlerini dizelere dönüştürme varsayılan türü dönüştürücü ile ilişkilendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="32a5c-113">Common data types are associated with default type converters that convert values into strings and strings into the appropriate data types.</span></span> <span data-ttu-id="32a5c-114">Özel bir özellik tanımlarsanız (diğer bir deyişle, standart olmayan) veri türü olacaktır bu özellik ile ilişkilendirmek için tür dönüştürücüsünü belirten bir özniteliği uygulamak.</span><span class="sxs-lookup"><span data-stu-id="32a5c-114">If you define a property that is a custom (that is, nonstandard) data type, you will have to apply an attribute that specifies the type converter to associate with that property.</span></span> <span data-ttu-id="32a5c-115">Öznitelik, bir Özel UI türü Düzenleyici özelliği ile ilişkilendirmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32a5c-115">You can also use an attribute to associate a custom UI type editor with a property.</span></span> <span data-ttu-id="32a5c-116">UI türü Düzenleyici bir özellik ya da veri türü düzenlemek için bir kullanıcı arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="32a5c-116">A UI type editor provides a user interface for editing a property or data type.</span></span> <span data-ttu-id="32a5c-117">Bir renk seçici UI türü Düzenleyici örneğidir.</span><span class="sxs-lookup"><span data-stu-id="32a5c-117">A color picker is an example of a UI type editor.</span></span> <span data-ttu-id="32a5c-118">Öznitelikleri örnekleri, bu konunun sonunda verilir.</span><span class="sxs-lookup"><span data-stu-id="32a5c-118">Examples of attributes are given at the end of this topic.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="32a5c-119">Tür dönüştürücüsünü veya UI türü Düzenleyici özel özellik için kullanılabilir değilse, bir açıklandığı gibi uygulayabileceğiniz [genişletme tasarım zamanı desteği](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).</span><span class="sxs-lookup"><span data-stu-id="32a5c-119">If a type converter or a UI type editor is not available for your custom property, you can implement one as described in [Extending Design-Time Support](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).</span></span>  
  
 <span data-ttu-id="32a5c-120">Aşağıdaki kod parçası adlı özel bir özelliğini tanımlar `EndColor` özel denetim için `FlashTrackBar`.</span><span class="sxs-lookup"><span data-stu-id="32a5c-120">The following code fragment defines a custom property named `EndColor` for the custom control `FlashTrackBar`.</span></span>  
  
```vb  
Public Class FlashTrackBar  
   Inherits Control  
   ...  
   ' Private data member that backs the EndColor property.  
   Private _endColor As Color = Color.LimeGreen  
  
   ' The Category attribute tells the designer to display  
   ' it in the Flash grouping.   
   ' The Description attribute provides a description of  
   ' the property.   
   <Category("Flash"), _  
   Description("The ending color of the bar.")>  _  
   Public Property EndColor() As Color  
      ' The public property EndColor accesses _endColor.  
      Get  
         Return _endColor  
      End Get  
      Set  
         _endColor = value  
         If Not (baseBackground Is Nothing) And showGradient Then  
            baseBackground.Dispose()  
            baseBackground = Nothing  
         End If  
         ' The Invalidate method calls the OnPaint method, which redraws    
         ' the control.  
         Invalidate()  
      End Set  
   End Property  
   ...  
End Class  
```  
  
```csharp  
public class FlashTrackBar : Control {  
   ...  
   // Private data member that backs the EndColor property.  
   private Color endColor = Color.LimeGreen;  
   // The Category attribute tells the designer to display  
   // it in the Flash grouping.   
   // The Description attribute provides a description of  
   // the property.   
   [  
   Category("Flash"),  
   Description("The ending color of the bar.")  
   ]  
   // The public property EndColor accesses endColor.  
   public Color EndColor {  
      get {  
         return endColor;  
      }  
      set {  
         endColor = value;  
         if (baseBackground != null && showGradient) {  
            baseBackground.Dispose();  
            baseBackground = null;  
         }  
         // The Invalidate method calls the OnPaint method, which redraws   
         // the control.  
         Invalidate();  
      }  
   }  
   ...  
}  
```  
  
 <span data-ttu-id="32a5c-121">Aşağıdaki kod parçası tür dönüştürücüsünü ve UI türü Düzenleyici özelliği ile ilişkilendiren `Value`.</span><span class="sxs-lookup"><span data-stu-id="32a5c-121">The following code fragment associates a type converter and a UI type editor with the property `Value`.</span></span> <span data-ttu-id="32a5c-122">Bu durumda `Value` bir tamsayı ve bir varsayılan türü dönüştürücü sahip ancak <xref:System.ComponentModel.TypeConverterAttribute> özniteliği geçerli bir özel tür dönüştürücüsünü (`FlashTrackBarValueConverter`) yüzde olarak görüntülemek tasarımcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="32a5c-122">In this case `Value` is an integer and has a default type converter, but the <xref:System.ComponentModel.TypeConverterAttribute> attribute applies a custom type converter (`FlashTrackBarValueConverter`) that enables the designer to display it as a percentage.</span></span> <span data-ttu-id="32a5c-123">UI türü düzenleyici `FlashTrackBarValueEditor`, görsel olarak görüntülenecek yüzdesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="32a5c-123">The UI type editor, `FlashTrackBarValueEditor`, allows the percentage to be displayed visually.</span></span> <span data-ttu-id="32a5c-124">Bu örnek ayrıca, tür dönüştürücüsünü veya Düzenleyicisi tarafından belirtilen gösterir <xref:System.ComponentModel.TypeConverterAttribute> veya <xref:System.ComponentModel.EditorAttribute> özniteliği varsayılan dönüştürücü geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="32a5c-124">This example also shows that the type converter or editor specified by the <xref:System.ComponentModel.TypeConverterAttribute> or <xref:System.ComponentModel.EditorAttribute> attribute overrides the default converter.</span></span>  
  
```vb  
<Category("Flash"), _  
TypeConverter(GetType(FlashTrackBarValueConverter)), _  
Editor(GetType(FlashTrackBarValueEditor), _  
GetType(UITypeEditor)), _  
Description("The current value of the track bar.  You can enter an actual value or a percentage.")>  _  
Public ReadOnly Property Value() As Integer  
...  
End Property  
```  
  
```csharp  
[  
Category("Flash"),   
TypeConverter(typeof(FlashTrackBarValueConverter)),  
Editor(typeof(FlashTrackBarValueEditor), typeof(UITypeEditor)),  
Description("The current value of the track bar.  You can enter an actual value or a percentage.")  
]  
public int Value {  
...  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="32a5c-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="32a5c-125">See Also</span></span>  
 [<span data-ttu-id="32a5c-126">Windows Forms Denetimlerindeki Özellikler</span><span class="sxs-lookup"><span data-stu-id="32a5c-126">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [<span data-ttu-id="32a5c-127">ShouldSerialize ile Varsayılan Değerleri Tanımlama ve Yöntemleri Sıfırlama</span><span class="sxs-lookup"><span data-stu-id="32a5c-127">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>](../../../../docs/framework/winforms/controls/defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 [<span data-ttu-id="32a5c-128">Özellik Değişti Olayları</span><span class="sxs-lookup"><span data-stu-id="32a5c-128">Property-Changed Events</span></span>](../../../../docs/framework/winforms/controls/property-changed-events.md)  
 [<span data-ttu-id="32a5c-129">Windows Forms Denetimlerindeki Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="32a5c-129">Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)
