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
ms.openlocfilehash: 0fec817226a7da4b44ec992f9e384a2ad5449001
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746099"
---
# <a name="defining-a-property-in-windows-forms-controls"></a>Windows Forms Denetimlerinde Özellik Tanımlama
Özelliklere genel bakış için bkz. [özelliklere genel bakış](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)). Bir özellik tanımlarken dikkat etmeniz gereken birkaç önemli nokta vardır:  
  
- Tanımladığınız özelliklere öznitelikler uygulamanız gerekir. Öznitelikler, tasarımcının bir özelliği nasıl görüntülemesi gerektiğini belirtir. Ayrıntılar için bkz. [Bileşenler Için tasarım zamanı öznitelikleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).  
  
- Özelliği değiştirmek denetimin görsel görüntüsünü etkiliyorsa, `set` erişimcisindeki <xref:System.Windows.Forms.Control.Invalidate%2A> yöntemini (denetiminizin <xref:System.Windows.Forms.Control>devraldığından) çağırın. <xref:System.Windows.Forms.Control.Invalidate%2A>, <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemini çağırır ve bu da denetimi yeniden çizer. <xref:System.Windows.Forms.Control.Invalidate%2A> birden çok çağrısı, verimlilik için <xref:System.Windows.Forms.Control.OnPaint%2A> tek bir çağrıda sonuçlanır.  
  
- .NET Framework sınıf kitaplığı, tamsayılar, ondalık sayılar, Boole değerleri ve diğerleri gibi ortak veri türleri için tür dönüştürücüler sağlar. Bir tür dönüştürücünün amacı genellikle dizeden değere dönüştürme (dize verilerinden diğer veri türlerine) sağlamaktır. Ortak veri türleri, değerleri dizelere ve dizilere uygun veri türlerine dönüştüren varsayılan tür dönüştürücülerle ilişkilendirilir. Özel (Standart olmayan) veri türü olan bir özellik tanımlarsanız, bu özellik ile ilişkilendirilecek tür dönüştürücüsünü belirten bir öznitelik uygulamanız gerekir. Özel bir UI türü düzenleyicisini bir özelliği ile ilişkilendirmek için de bir özniteliği kullanabilirsiniz. Kullanıcı arabirimi tür Düzenleyicisi, bir özellik veya veri türü düzenleme için bir kullanıcı arabirimi sağlar. Renk Seçici, UI türü düzenleyicinin bir örneğidir. Bu konunun sonunda özniteliklerin örnekleri verilmiştir.  
  
    > [!NOTE]
    > Özel özellik için bir tür dönüştürücü veya Kullanıcı arabirimi türü Düzenleyicisi yoksa, [Tasarım zamanı desteğini genişletme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))bölümünde açıklandığı gibi bir tane uygulayabilirsiniz.  
  
 Aşağıdaki kod parçası, özel denetim `FlashTrackBar`için `EndColor` adlı özel bir özelliği tanımlar.  
  
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
  
 Aşağıdaki kod parçası, bir tür dönüştürücüsünü ve Kullanıcı arabirimi tür düzenleyicisini `Value`özellik ile ilişkilendirir. Bu durumda `Value` bir tamsayıdır ve varsayılan bir tür dönüştürücüde bulunur, ancak <xref:System.ComponentModel.TypeConverterAttribute> özniteliği tasarımcının bir yüzde olarak görüntülenmesini sağlayan özel bir tür Dönüştürücüsü (`FlashTrackBarValueConverter`) uygular. `FlashTrackBarValueEditor`Kullanıcı arabirimi tür Düzenleyicisi, yüzdenin görsel olarak görüntülenmesine izin verir. Bu örnek ayrıca, <xref:System.ComponentModel.TypeConverterAttribute> veya <xref:System.ComponentModel.EditorAttribute> özniteliği tarafından belirtilen tür dönüştürücüsünün ya da düzenleyicinin varsayılan dönüştürücüyü geçersiz kıldığını gösterir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms Denetimlerindeki Özellikler](properties-in-windows-forms-controls.md)
- [ShouldSerialize ile Varsayılan Değerleri Tanımlama ve Yöntemleri Sıfırlama](defining-default-values-with-the-shouldserialize-and-reset-methods.md)
- [Özellik Değişti Olayları](property-changed-events.md)
- [Windows Forms Denetimlerindeki Öznitelikler](attributes-in-windows-forms-controls.md)
