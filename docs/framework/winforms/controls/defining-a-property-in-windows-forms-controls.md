---
title: Denetim özelliklerini tanımlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [Windows Forms], defining in code
- custom controls [Windows Forms], defining properties in code
ms.assetid: c2eb8277-a842-4d99-89a9-647b901a0434
ms.openlocfilehash: 7223f8c88bee4ee9c1db621cc39bbcf70d0c4589
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182381"
---
# <a name="defining-a-property-in-windows-forms-controls"></a><span data-ttu-id="b5fa8-102">Windows Forms Denetimlerinde Özellik Tanımlama</span><span class="sxs-lookup"><span data-stu-id="b5fa8-102">Defining a Property in Windows Forms Controls</span></span>
<span data-ttu-id="b5fa8-103">Özelliklere genel bakış için [bkz.](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="b5fa8-103">For an overview of properties, see [Properties Overview](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)).</span></span> <span data-ttu-id="b5fa8-104">Bir özelliği tanımlarken göz önünde bulundurulması gereken birkaç önemli husus vardır:</span><span class="sxs-lookup"><span data-stu-id="b5fa8-104">There are a few important considerations when defining a property:</span></span>  
  
- <span data-ttu-id="b5fa8-105">Öznitelikleri tanımladığınız özelliklere uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b5fa8-105">You must apply attributes to the properties you define.</span></span> <span data-ttu-id="b5fa8-106">Öznitelikler, tasarımcının bir özelliği nasıl görüntülemesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b5fa8-106">Attributes specify how the designer should display a property.</span></span> <span data-ttu-id="b5fa8-107">Ayrıntılar için, [Bileşenler için Tasarım-Zaman Öznitelikleri'ne](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))bakın.</span><span class="sxs-lookup"><span data-stu-id="b5fa8-107">For details, see [Design-Time Attributes for Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).</span></span>  
  
- <span data-ttu-id="b5fa8-108">Özelliği değiştirmek denetimin görsel ekranını etkiliyorsa, <xref:System.Windows.Forms.Control.Invalidate%2A> <xref:System.Windows.Forms.Control> `set` erişimciden (denetiminizin devraldığı) yöntemi arayın.</span><span class="sxs-lookup"><span data-stu-id="b5fa8-108">If changing the property affects the visual display of the control, call the <xref:System.Windows.Forms.Control.Invalidate%2A> method (that your control inherits from <xref:System.Windows.Forms.Control>) from the `set` accessor.</span></span> <span data-ttu-id="b5fa8-109"><xref:System.Windows.Forms.Control.Invalidate%2A>sırayla denetimi <xref:System.Windows.Forms.Control.OnPaint%2A> yeniden çizen yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="b5fa8-109"><xref:System.Windows.Forms.Control.Invalidate%2A> in turn calls the <xref:System.Windows.Forms.Control.OnPaint%2A> method, which redraws the control.</span></span> <span data-ttu-id="b5fa8-110">Verimlilik için <xref:System.Windows.Forms.Control.Invalidate%2A> tek bir çağrı <xref:System.Windows.Forms.Control.OnPaint%2A> yla sonuçlanması için birden çok çağrı.</span><span class="sxs-lookup"><span data-stu-id="b5fa8-110">Multiple calls to <xref:System.Windows.Forms.Control.Invalidate%2A> result in a single call to <xref:System.Windows.Forms.Control.OnPaint%2A> for efficiency.</span></span>  
  
- <span data-ttu-id="b5fa8-111">.NET Framework sınıf kitaplığı, tamsayılar, ondalık sayılar, Boolean değerleri ve diğerleri gibi yaygın veri türleri için tür dönüştürücüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b5fa8-111">The .NET Framework class library provides type converters for common data types such as integers, decimal numbers, Boolean values, and others.</span></span> <span data-ttu-id="b5fa8-112">Tür dönüştürücünün amacı genellikle dize-değer dönüştürme (dize verilerinden diğer veri türlerine) sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="b5fa8-112">The purpose of a type converter is generally to provide string-to-value conversion (from string data to other data types).</span></span> <span data-ttu-id="b5fa8-113">Yaygın veri türleri, değerleri dizeleri ve dizeleri uygun veri türlerine dönüştüren varsayılan tür dönüştürücülerle ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="b5fa8-113">Common data types are associated with default type converters that convert values into strings and strings into the appropriate data types.</span></span> <span data-ttu-id="b5fa8-114">Özel (yani standart dışı) bir özellik tanımlarsanız, bu özellik ile ilişkilendirmek için tür dönüştürücü belirten bir öznitelik uygulamak zorunda kalacaktır.</span><span class="sxs-lookup"><span data-stu-id="b5fa8-114">If you define a property that is a custom (that is, nonstandard) data type, you will have to apply an attribute that specifies the type converter to associate with that property.</span></span> <span data-ttu-id="b5fa8-115">Özel bir Kullanıcı Arabirimi türü düzenleyicisini bir özellikle ilişkilendirmek için bir öznitelik de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5fa8-115">You can also use an attribute to associate a custom UI type editor with a property.</span></span> <span data-ttu-id="b5fa8-116">Kullanıcı Arabirimi türü düzenleyicisi, bir özelliği veya veri türünü düzenlemek için bir kullanıcı arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b5fa8-116">A UI type editor provides a user interface for editing a property or data type.</span></span> <span data-ttu-id="b5fa8-117">Renk seçici, ui türü düzenleyicisine bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="b5fa8-117">A color picker is an example of a UI type editor.</span></span> <span data-ttu-id="b5fa8-118">Bu konunun sonunda özniteliklere örnekler verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b5fa8-118">Examples of attributes are given at the end of this topic.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b5fa8-119">Özel mülkünüz için bir tür dönüştürücü veya kullanıcı arabirimi türü düzenleyicisi kullanılamıyorsa, [Tasarım-Zaman Desteğini Genişletme'de](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))açıklandığı gibi bir tane uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5fa8-119">If a type converter or a UI type editor is not available for your custom property, you can implement one as described in [Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120)).</span></span>  
  
 <span data-ttu-id="b5fa8-120">Aşağıdaki kod parçası özel denetim `EndColor` `FlashTrackBar`için adlı özel bir özellik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b5fa8-120">The following code fragment defines a custom property named `EndColor` for the custom control `FlashTrackBar`.</span></span>  
  
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
  
 <span data-ttu-id="b5fa8-121">Aşağıdaki kod parçası, bir tür dönüştürücü ve bir `Value`UI türü düzenleyiciözelliği ile ilişkilendiriler.</span><span class="sxs-lookup"><span data-stu-id="b5fa8-121">The following code fragment associates a type converter and a UI type editor with the property `Value`.</span></span> <span data-ttu-id="b5fa8-122">Bu durumda `Value` bir tamsayı dır ve varsayılan tür dönüştürücüsi vardır, ancak <xref:System.ComponentModel.TypeConverterAttribute> öznitelik, tasarımcının bunu yüzde olarak görüntülemesini sağlayan özel bir tür dönüştürücü (`FlashTrackBarValueConverter`) uygular.</span><span class="sxs-lookup"><span data-stu-id="b5fa8-122">In this case `Value` is an integer and has a default type converter, but the <xref:System.ComponentModel.TypeConverterAttribute> attribute applies a custom type converter (`FlashTrackBarValueConverter`) that enables the designer to display it as a percentage.</span></span> <span data-ttu-id="b5fa8-123">Kullanıcı Arabirimi türü `FlashTrackBarValueEditor`düzenleyicisi, yüzdenin görsel olarak görüntülenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b5fa8-123">The UI type editor, `FlashTrackBarValueEditor`, allows the percentage to be displayed visually.</span></span> <span data-ttu-id="b5fa8-124">Bu örnek, tür dönüştürücü veya düzenleyici <xref:System.ComponentModel.TypeConverterAttribute> tarafından <xref:System.ComponentModel.EditorAttribute> belirtilen veya öznitelik varsayılan dönüştürücü geçersiz kılar gösterir.</span><span class="sxs-lookup"><span data-stu-id="b5fa8-124">This example also shows that the type converter or editor specified by the <xref:System.ComponentModel.TypeConverterAttribute> or <xref:System.ComponentModel.EditorAttribute> attribute overrides the default converter.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b5fa8-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5fa8-125">See also</span></span>

- [<span data-ttu-id="b5fa8-126">Windows Forms Denetimlerindeki Özellikler</span><span class="sxs-lookup"><span data-stu-id="b5fa8-126">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
- [<span data-ttu-id="b5fa8-127">ShouldSerialize ile Varsayılan Değerleri Tanımlama ve Yöntemleri Sıfırlama</span><span class="sxs-lookup"><span data-stu-id="b5fa8-127">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>](defining-default-values-with-the-shouldserialize-and-reset-methods.md)
- [<span data-ttu-id="b5fa8-128">Özellik Değişti Olayları</span><span class="sxs-lookup"><span data-stu-id="b5fa8-128">Property-Changed Events</span></span>](property-changed-events.md)
- [<span data-ttu-id="b5fa8-129">Windows Forms Denetimlerindeki Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b5fa8-129">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)
