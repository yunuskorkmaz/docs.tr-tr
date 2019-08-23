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
ms.openlocfilehash: a641b1e7565842a1edf6aeec88bdc37ee0786ab4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969124"
---
# <a name="defining-a-property-in-windows-forms-controls"></a><span data-ttu-id="adaaf-102">Windows Forms Denetimlerinde Özellik Tanımlama</span><span class="sxs-lookup"><span data-stu-id="adaaf-102">Defining a Property in Windows Forms Controls</span></span>
<span data-ttu-id="adaaf-103">Özelliklere genel bakış için bkz. [özelliklere genel bakış](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="adaaf-103">For an overview of properties, see [Properties Overview](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)).</span></span> <span data-ttu-id="adaaf-104">Bir özellik tanımlarken dikkat etmeniz gereken birkaç önemli nokta vardır:</span><span class="sxs-lookup"><span data-stu-id="adaaf-104">There are a few important considerations when defining a property:</span></span>  
  
- <span data-ttu-id="adaaf-105">Tanımladığınız özelliklere öznitelikler uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="adaaf-105">You must apply attributes to the properties you define.</span></span> <span data-ttu-id="adaaf-106">Öznitelikler, tasarımcının bir özelliği nasıl görüntülemesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="adaaf-106">Attributes specify how the designer should display a property.</span></span> <span data-ttu-id="adaaf-107">Ayrıntılar için bkz. [Bileşenler Için tasarım zamanı öznitelikleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="adaaf-107">For details, see [Design-Time Attributes for Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).</span></span>  
  
- <span data-ttu-id="adaaf-108">Özelliği değiştirmek denetimin görsel görüntüsünü etkiliyorsa, <xref:System.Windows.Forms.Control.Invalidate%2A> `set` erişimcinden (denetiminizin <xref:System.Windows.Forms.Control>Devralındığı) yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="adaaf-108">If changing the property affects the visual display of the control, call the <xref:System.Windows.Forms.Control.Invalidate%2A> method (that your control inherits from <xref:System.Windows.Forms.Control>) from the `set` accessor.</span></span> <span data-ttu-id="adaaf-109"><xref:System.Windows.Forms.Control.Invalidate%2A>öğesinde, denetimi yeniden <xref:System.Windows.Forms.Control.OnPaint%2A> gösteren yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="adaaf-109"><xref:System.Windows.Forms.Control.Invalidate%2A> in turn calls the <xref:System.Windows.Forms.Control.OnPaint%2A> method, which redraws the control.</span></span> <span data-ttu-id="adaaf-110">Birden çok çağrı <xref:System.Windows.Forms.Control.Invalidate%2A> , verimlilik <xref:System.Windows.Forms.Control.OnPaint%2A> için tek bir çağrıda sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="adaaf-110">Multiple calls to <xref:System.Windows.Forms.Control.Invalidate%2A> result in a single call to <xref:System.Windows.Forms.Control.OnPaint%2A> for efficiency.</span></span>  
  
- <span data-ttu-id="adaaf-111">.NET Framework sınıf kitaplığı, tamsayılar, ondalık sayılar, Boole değerleri ve diğerleri gibi ortak veri türleri için tür dönüştürücüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="adaaf-111">The .NET Framework class library provides type converters for common data types such as integers, decimal numbers, Boolean values, and others.</span></span> <span data-ttu-id="adaaf-112">Bir tür dönüştürücünün amacı genellikle dizeden değere dönüştürme (dize verilerinden diğer veri türlerine) sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="adaaf-112">The purpose of a type converter is generally to provide string-to-value conversion (from string data to other data types).</span></span> <span data-ttu-id="adaaf-113">Ortak veri türleri, değerleri dizelere ve dizilere uygun veri türlerine dönüştüren varsayılan tür dönüştürücülerle ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="adaaf-113">Common data types are associated with default type converters that convert values into strings and strings into the appropriate data types.</span></span> <span data-ttu-id="adaaf-114">Özel (Standart olmayan) veri türü olan bir özellik tanımlarsanız, bu özellik ile ilişkilendirilecek tür dönüştürücüsünü belirten bir öznitelik uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="adaaf-114">If you define a property that is a custom (that is, nonstandard) data type, you will have to apply an attribute that specifies the type converter to associate with that property.</span></span> <span data-ttu-id="adaaf-115">Özel bir UI türü düzenleyicisini bir özelliği ile ilişkilendirmek için de bir özniteliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="adaaf-115">You can also use an attribute to associate a custom UI type editor with a property.</span></span> <span data-ttu-id="adaaf-116">Kullanıcı arabirimi tür Düzenleyicisi, bir özellik veya veri türü düzenleme için bir kullanıcı arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="adaaf-116">A UI type editor provides a user interface for editing a property or data type.</span></span> <span data-ttu-id="adaaf-117">Renk Seçici, UI türü düzenleyicinin bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="adaaf-117">A color picker is an example of a UI type editor.</span></span> <span data-ttu-id="adaaf-118">Bu konunun sonunda özniteliklerin örnekleri verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="adaaf-118">Examples of attributes are given at the end of this topic.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="adaaf-119">Özel özellik için bir tür dönüştürücü veya Kullanıcı arabirimi türü Düzenleyicisi yoksa, [Tasarım zamanı desteğini genişletme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))bölümünde açıklandığı gibi bir tane uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="adaaf-119">If a type converter or a UI type editor is not available for your custom property, you can implement one as described in [Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120)).</span></span>  
  
 <span data-ttu-id="adaaf-120">Aşağıdaki kod parçası, özel denetim `EndColor` `FlashTrackBar`için adlı özel bir özelliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="adaaf-120">The following code fragment defines a custom property named `EndColor` for the custom control `FlashTrackBar`.</span></span>  
  
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
  
 <span data-ttu-id="adaaf-121">Aşağıdaki kod parçası, bir tür dönüştürücüsünü ve bir UI türü düzenleyicisini özelliği `Value`ile ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="adaaf-121">The following code fragment associates a type converter and a UI type editor with the property `Value`.</span></span> <span data-ttu-id="adaaf-122">Bu örnekte `Value` bir tamsayı ve varsayılan bir tür dönüştürücüsü vardır <xref:System.ComponentModel.TypeConverterAttribute> ancak öznitelik, tasarımcının bir yüzde olarak görüntülenmesini sağlayan özel bir tür`FlashTrackBarValueConverter`Dönüştürücüsü () uygular.</span><span class="sxs-lookup"><span data-stu-id="adaaf-122">In this case `Value` is an integer and has a default type converter, but the <xref:System.ComponentModel.TypeConverterAttribute> attribute applies a custom type converter (`FlashTrackBarValueConverter`) that enables the designer to display it as a percentage.</span></span> <span data-ttu-id="adaaf-123">UI türü Düzenleyici `FlashTrackBarValueEditor`, yüzdenin görsel olarak görüntülenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="adaaf-123">The UI type editor, `FlashTrackBarValueEditor`, allows the percentage to be displayed visually.</span></span> <span data-ttu-id="adaaf-124">Bu örnek ayrıca, <xref:System.ComponentModel.TypeConverterAttribute> ya <xref:System.ComponentModel.EditorAttribute> da özniteliği tarafından belirtilen tür dönüştürücüsünün ya da düzenleyicinin varsayılan dönüştürücüyü geçersiz kıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="adaaf-124">This example also shows that the type converter or editor specified by the <xref:System.ComponentModel.TypeConverterAttribute> or <xref:System.ComponentModel.EditorAttribute> attribute overrides the default converter.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="adaaf-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="adaaf-125">See also</span></span>

- [<span data-ttu-id="adaaf-126">Windows Forms Denetimlerindeki Özellikler</span><span class="sxs-lookup"><span data-stu-id="adaaf-126">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
- [<span data-ttu-id="adaaf-127">ShouldSerialize ile Varsayılan Değerleri Tanımlama ve Yöntemleri Sıfırlama</span><span class="sxs-lookup"><span data-stu-id="adaaf-127">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>](defining-default-values-with-the-shouldserialize-and-reset-methods.md)
- [<span data-ttu-id="adaaf-128">Özellik Değişti Olayları</span><span class="sxs-lookup"><span data-stu-id="adaaf-128">Property-Changed Events</span></span>](property-changed-events.md)
- [<span data-ttu-id="adaaf-129">Windows Forms Denetimlerindeki Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="adaaf-129">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)
