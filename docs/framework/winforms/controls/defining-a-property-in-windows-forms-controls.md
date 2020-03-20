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
# <a name="defining-a-property-in-windows-forms-controls"></a>Windows Forms Denetimlerinde Özellik Tanımlama
Özelliklere genel bakış için [bkz.](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)) Bir özelliği tanımlarken göz önünde bulundurulması gereken birkaç önemli husus vardır:  
  
- Öznitelikleri tanımladığınız özelliklere uygulamanız gerekir. Öznitelikler, tasarımcının bir özelliği nasıl görüntülemesi gerektiğini belirtir. Ayrıntılar için, [Bileşenler için Tasarım-Zaman Öznitelikleri'ne](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))bakın.  
  
- Özelliği değiştirmek denetimin görsel ekranını etkiliyorsa, <xref:System.Windows.Forms.Control.Invalidate%2A> <xref:System.Windows.Forms.Control> `set` erişimciden (denetiminizin devraldığı) yöntemi arayın. <xref:System.Windows.Forms.Control.Invalidate%2A>sırayla denetimi <xref:System.Windows.Forms.Control.OnPaint%2A> yeniden çizen yöntemi çağırır. Verimlilik için <xref:System.Windows.Forms.Control.Invalidate%2A> tek bir çağrı <xref:System.Windows.Forms.Control.OnPaint%2A> yla sonuçlanması için birden çok çağrı.  
  
- .NET Framework sınıf kitaplığı, tamsayılar, ondalık sayılar, Boolean değerleri ve diğerleri gibi yaygın veri türleri için tür dönüştürücüler sağlar. Tür dönüştürücünün amacı genellikle dize-değer dönüştürme (dize verilerinden diğer veri türlerine) sağlamaktır. Yaygın veri türleri, değerleri dizeleri ve dizeleri uygun veri türlerine dönüştüren varsayılan tür dönüştürücülerle ilişkilidir. Özel (yani standart dışı) bir özellik tanımlarsanız, bu özellik ile ilişkilendirmek için tür dönüştürücü belirten bir öznitelik uygulamak zorunda kalacaktır. Özel bir Kullanıcı Arabirimi türü düzenleyicisini bir özellikle ilişkilendirmek için bir öznitelik de kullanabilirsiniz. Kullanıcı Arabirimi türü düzenleyicisi, bir özelliği veya veri türünü düzenlemek için bir kullanıcı arabirimi sağlar. Renk seçici, ui türü düzenleyicisine bir örnektir. Bu konunun sonunda özniteliklere örnekler verilmiştir.  
  
    > [!NOTE]
    > Özel mülkünüz için bir tür dönüştürücü veya kullanıcı arabirimi türü düzenleyicisi kullanılamıyorsa, [Tasarım-Zaman Desteğini Genişletme'de](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))açıklandığı gibi bir tane uygulayabilirsiniz.  
  
 Aşağıdaki kod parçası özel denetim `EndColor` `FlashTrackBar`için adlı özel bir özellik tanımlar.  
  
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
  
 Aşağıdaki kod parçası, bir tür dönüştürücü ve bir `Value`UI türü düzenleyiciözelliği ile ilişkilendiriler. Bu durumda `Value` bir tamsayı dır ve varsayılan tür dönüştürücüsi vardır, ancak <xref:System.ComponentModel.TypeConverterAttribute> öznitelik, tasarımcının bunu yüzde olarak görüntülemesini sağlayan özel bir tür dönüştürücü (`FlashTrackBarValueConverter`) uygular. Kullanıcı Arabirimi türü `FlashTrackBarValueEditor`düzenleyicisi, yüzdenin görsel olarak görüntülenmesini sağlar. Bu örnek, tür dönüştürücü veya düzenleyici <xref:System.ComponentModel.TypeConverterAttribute> tarafından <xref:System.ComponentModel.EditorAttribute> belirtilen veya öznitelik varsayılan dönüştürücü geçersiz kılar gösterir.  
  
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
