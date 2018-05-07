---
title: Özel Denetimlerde Yöntem Uygulama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user controls [Windows Forms], method implementation
- custom controls [Windows Forms], overloading methods
- custom controls [Windows Forms], method implementation
- methods [Windows Forms]
- methods [Windows Forms], custom controls
ms.assetid: 35d14fca-4bb4-4a27-8211-1f7a98ea27de
ms.openlocfilehash: 9df2bc9257c3f697f30cbe8c679ffc88ec34517b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="method-implementation-in-custom-controls"></a>Özel Denetimlerde Yöntem Uygulama
Bir yöntem bir denetimde bir yöntem içindeki herhangi bir bileşen uygulanması aynı şekilde uygulanır.  
  
 Bir yöntem için bir değer döndürmek için gerekliyse, Visual Basic'te şu olarak uygulanan bir `Public Function`. Herhangi bir değer döndürürse, olarak uygulandığı bir `Public Sub`. Yöntemleri aşağıdaki sözdizimini kullanarak bildirilir:  
  
```vb  
Public Function ConvertMatterToEnergy(Matter as Integer) As Integer  
   ' Conversion code goes here.  
End Function  
```  
  
 İşlevler bir değer döndürür olduğundan, tamsayı, dize, nesne vb. gibi bir dönüş türü belirtmeniz gerekir. Bağımsız değişkenler `Function` veya `Sub` herhangi biri, aynı zamanda belirtilmesi gerekir, yordamları gerçekleştirin.  
  
 Visual Basic yaptığı gibi C# işlevleri ve yordamlar arasında ayrım sağlar. Bir yöntemi bir değer döndürür veya verir `void`. Bir C# genel yöntem bildirmek için sözdizimi aşağıdaki gibidir:  
  
```csharp  
public int ConvertMatterToEnergy(int matter)  
{  
   // Conversion code goes here.  
}  
```  
  
 Bir yöntem bildirin, tüm bağımsız değişkenlerinin açık veri türleri olarak mümkün olduğunca bildirin. Nesne başvuruları ele bağımsız değişkenleri belirli bir sınıf türü olarak bildirilmiş — Örneğin, `As Widget` yerine `As Object`. Visual Basic'de varsayılan ayar `Option Strict` otomatik olarak bu kural zorlar.  
  
 Yazılı bağımsız değişkenler derleyici yerine çalışma zamanında Yakalanacak birçok geliştirici hata izin verir. Çalışma zamanı test yalnızca test paketi kadar iyi iken derleyici hataları, her zaman yakalar.  
  
## <a name="overloaded-methods"></a>Aşırı yüklenmiş yöntemler  
 Farklı bir yöntem için parametre birleşimleri sağlamak kullanıcıların denetiminizin izin vermek istiyorsanız, birden çok aşırı açık veri türlerini kullanma yöntem sağlar. Bildirilen parametreleri oluşturmamak `As Object` , içerebilir herhangi bir veri türü olarak bu testinde yakalandı hatalara yol açabilir.  
  
> [!NOTE]
>  Ortak dil çalışma zamanında evrensel veri türü `Object` yerine `Variant`. `Variant` dilden kaldırılmıştır.  
  
 Örneğin, `Spin` bir kuramsal yöntemi `Widget` denetimi izin döndürme yön ve hız doğrudan belirtimi ya da başka bir belirtim `Widget` hangi angular satışlarının nesnesinden olduğu absorbed olmalıdır:  
  
```vb  
Overloads Public Sub Spin( _  
   ByVal SpinDirection As SpinDirectionsEnum, _  
   ByVal RevolutionsPerSecond As Double)  
   ' Implementation code here.  
End Sub  
Overloads Public Sub Spin(ByVal Driver As Widget) _  
   ' Implementation code here.  
End Sub  
```  
  
```csharp  
public void Spin(SpinDirectionsEnum spinDirection, double revolutionsPerSecond)  
{  
   // Implementation code here.  
}  
  
public void Spin(Widget driver)  
{  
   // Implementation code here.  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Olaylar](../../../../docs/standard/events/index.md)  
 [Windows Forms Denetimlerindeki Özellikler](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)
