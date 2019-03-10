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
ms.openlocfilehash: 84273d2fab36df287eaca70f5f32fd8024a9204d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57712207"
---
# <a name="defining-a-property-in-windows-forms-controls"></a><span data-ttu-id="a4a06-102">Windows Forms Denetimlerinde Özellik Tanımlama</span><span class="sxs-lookup"><span data-stu-id="a4a06-102">Defining a Property in Windows Forms Controls</span></span>
<span data-ttu-id="a4a06-103">Özellikleri genel bakış için bkz. [özelliklerine genel bakış](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="a4a06-103">For an overview of properties, see [Properties Overview](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)).</span></span> <span data-ttu-id="a4a06-104">Bir özellik tanımlarken birkaç önemli nokta vardır:</span><span class="sxs-lookup"><span data-stu-id="a4a06-104">There are a few important considerations when defining a property:</span></span>  
  
-   <span data-ttu-id="a4a06-105">Özellikleri için tanımladığınız öznitelikleri uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a4a06-105">You must apply attributes to the properties you define.</span></span> <span data-ttu-id="a4a06-106">Bir özellik Tasarımcısı'nı nasıl görüntülenmelidir öznitelikleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="a4a06-106">Attributes specify how the designer should display a property.</span></span> <span data-ttu-id="a4a06-107">Ayrıntılar için bkz [bileşenler için tasarım zamanı öznitelikleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="a4a06-107">For details, see [Design-Time Attributes for Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).</span></span>  
  
-   <span data-ttu-id="a4a06-108">Özelliği değiştirmeyi denetimin görünümünü etkiler, çağrı <xref:System.Windows.Forms.Control.Invalidate%2A> yöntemi (denetiminiz devralınan <xref:System.Windows.Forms.Control>) öğesinden `set` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="a4a06-108">If changing the property affects the visual display of the control, call the <xref:System.Windows.Forms.Control.Invalidate%2A> method (that your control inherits from <xref:System.Windows.Forms.Control>) from the `set` accessor.</span></span> <span data-ttu-id="a4a06-109"><xref:System.Windows.Forms.Control.Invalidate%2A> sırayla çağırır <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi denetimi yeniden çizer.</span><span class="sxs-lookup"><span data-stu-id="a4a06-109"><xref:System.Windows.Forms.Control.Invalidate%2A> in turn calls the <xref:System.Windows.Forms.Control.OnPaint%2A> method, which redraws the control.</span></span> <span data-ttu-id="a4a06-110">Birden çok çağrılar <xref:System.Windows.Forms.Control.Invalidate%2A> sonucu tek bir çağrıda <xref:System.Windows.Forms.Control.OnPaint%2A> verimlilik için.</span><span class="sxs-lookup"><span data-stu-id="a4a06-110">Multiple calls to <xref:System.Windows.Forms.Control.Invalidate%2A> result in a single call to <xref:System.Windows.Forms.Control.OnPaint%2A> for efficiency.</span></span>  
  
-   <span data-ttu-id="a4a06-111">.NET Framework sınıf kitaplığı, tamsayı, ondalık sayılar, Boole değerleri ve diğerleri gibi ortak veri türleri için tür dönüştürücüleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="a4a06-111">The .NET Framework class library provides type converters for common data types such as integers, decimal numbers, Boolean values, and others.</span></span> <span data-ttu-id="a4a06-112">Genellikle amacı bir tür dönüştürücüsü, dize değeri dönüştürme (gelen dize verileri diğer veri türleri için) sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="a4a06-112">The purpose of a type converter is generally to provide string-to-value conversion (from string data to other data types).</span></span> <span data-ttu-id="a4a06-113">Ortak veri türleri, değerleri dizeler ve uygun veri türlerini dizelere dönüştürme varsayılan tür dönüştürücüleri ile ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="a4a06-113">Common data types are associated with default type converters that convert values into strings and strings into the appropriate data types.</span></span> <span data-ttu-id="a4a06-114">Özel bir özellik tanımlarsanız (diğer bir deyişle, standart dışı) veri türü, bu özellik ile ilişkilendirilecek tür dönüştürücüsünü belirten bir öznitelik uygulamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="a4a06-114">If you define a property that is a custom (that is, nonstandard) data type, you will have to apply an attribute that specifies the type converter to associate with that property.</span></span> <span data-ttu-id="a4a06-115">Bir öznitelik, bir Özel UI türü Düzenleyici bir özellik ile ilişkilendirmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4a06-115">You can also use an attribute to associate a custom UI type editor with a property.</span></span> <span data-ttu-id="a4a06-116">UI türü Düzenleyici, özellik ya da veri türünü düzenlemek için bir kullanıcı arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a4a06-116">A UI type editor provides a user interface for editing a property or data type.</span></span> <span data-ttu-id="a4a06-117">Bir renk seçici, UI türü Düzenleyici örneğidir.</span><span class="sxs-lookup"><span data-stu-id="a4a06-117">A color picker is an example of a UI type editor.</span></span> <span data-ttu-id="a4a06-118">Bu konunun sonunda öznitelikleri örnekleri verilir.</span><span class="sxs-lookup"><span data-stu-id="a4a06-118">Examples of attributes are given at the end of this topic.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a4a06-119">Bir tür dönüştürücüsü veya UI türü Düzenleyici, özel bir özellik için kullanılabilir değilse, bir bölümünde anlatıldığı gibi uygulayabileceğiniz [tasarım zamanı desteğini genişletmek](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="a4a06-119">If a type converter or a UI type editor is not available for your custom property, you can implement one as described in [Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120)).</span></span>  
  
 <span data-ttu-id="a4a06-120">Aşağıdaki kod parçası adlı bir özel özellik tanımlar `EndColor` özel denetim için `FlashTrackBar`.</span><span class="sxs-lookup"><span data-stu-id="a4a06-120">The following code fragment defines a custom property named `EndColor` for the custom control `FlashTrackBar`.</span></span>  
  
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
  
 <span data-ttu-id="a4a06-121">Aşağıdaki kod parçası bir tür dönüştürücüsü ve UI türü Düzenleyici özelliğiyle ilişkilendirir `Value`.</span><span class="sxs-lookup"><span data-stu-id="a4a06-121">The following code fragment associates a type converter and a UI type editor with the property `Value`.</span></span> <span data-ttu-id="a4a06-122">Bu durumda `Value` tamsayı ve bir varsayılan tür dönüştürücüsü ancak <xref:System.ComponentModel.TypeConverterAttribute> özniteliği geçerli bir özel tür dönüştürücüsü (`FlashTrackBarValueConverter`) yüzde olarak görüntülemek tasarımcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a4a06-122">In this case `Value` is an integer and has a default type converter, but the <xref:System.ComponentModel.TypeConverterAttribute> attribute applies a custom type converter (`FlashTrackBarValueConverter`) that enables the designer to display it as a percentage.</span></span> <span data-ttu-id="a4a06-123">UI türü düzenleyici `FlashTrackBarValueEditor`, görsel olarak görüntülenecek yüzdesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a4a06-123">The UI type editor, `FlashTrackBarValueEditor`, allows the percentage to be displayed visually.</span></span> <span data-ttu-id="a4a06-124">Bu örnek ayrıca, bir tür dönüştürücüsü veya Düzenleyicisi tarafından belirtilen gösterir <xref:System.ComponentModel.TypeConverterAttribute> veya <xref:System.ComponentModel.EditorAttribute> öznitelik varsayılan dönüştürücü geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="a4a06-124">This example also shows that the type converter or editor specified by the <xref:System.ComponentModel.TypeConverterAttribute> or <xref:System.ComponentModel.EditorAttribute> attribute overrides the default converter.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a4a06-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4a06-125">See also</span></span>
- [<span data-ttu-id="a4a06-126">Windows Forms Denetimlerindeki Özellikler</span><span class="sxs-lookup"><span data-stu-id="a4a06-126">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
- [<span data-ttu-id="a4a06-127">ShouldSerialize ile Varsayılan Değerleri Tanımlama ve Yöntemleri Sıfırlama</span><span class="sxs-lookup"><span data-stu-id="a4a06-127">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>](defining-default-values-with-the-shouldserialize-and-reset-methods.md)
- [<span data-ttu-id="a4a06-128">Özellik Değişti Olayları</span><span class="sxs-lookup"><span data-stu-id="a4a06-128">Property-Changed Events</span></span>](property-changed-events.md)
- [<span data-ttu-id="a4a06-129">Windows Forms Denetimlerindeki Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a4a06-129">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)
