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
ms.openlocfilehash: f65c34c965ddf19c7a287eeeaafe2583c97583ef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506076"
---
# <a name="method-implementation-in-custom-controls"></a>Özel Denetimlerde Yöntem Uygulama
Bir yöntem bir denetimde bir yöntem içinde başka bir bileşen uygulanması aynı şekilde uygulanır.  
  
 Bir yöntem bir değer döndürmesi gerekiyorsa Visual Basic'te olarak uygulandığı bir `Public Function`. Herhangi bir değer döndürülürse, olarak uygulandığı bir `Public Sub`. Yöntemleri, aşağıdaki sözdizimini kullanarak bildirilir:  
  
```vb  
Public Function ConvertMatterToEnergy(Matter as Integer) As Integer  
   ' Conversion code goes here.  
End Function  
```  
  
 İşlevler bir değer döndürdüğünden, tamsayı, dize, nesne ve benzeri gibi bir dönüş türü belirtmeniz gerekir. Bağımsız değişkenler `Function` veya `Sub` herhangi biri, ayrıca belirtilmesi gerekir, yordamları Al.  
  
 C#Visual Basic gibi işlevleri ve yordamları arasında bir ayrım yapar. Bir yöntem bir değer döndürür veya döndürür `void`. Bildirmek için söz dizimi bir C# genel yöntemdir:  
  
```csharp  
public int ConvertMatterToEnergy(int matter)  
{  
   // Conversion code goes here.  
}  
```  
  
 Tüm bağımsız değişkenleri, bir yöntem bildirdiğinizde, mümkün olduğunda açık veri türleri olarak bildirin. Nesne başvurularını alan bağımsız değişkenleri belirli sınıf türleri bildirilmelidir — Örneğin, `As Widget` yerine `As Object`. Visual Basic'te, varsayılan ayarı `Option Strict` otomatik olarak bu kural uygular.  
  
 Yazılı bağımsız değişkenler, birçok geliştirici hataları çalışma zamanında değil, derleyici tarafından yakalanan izin verin. Çalışma zamanı sınaması yalnızca test paketi iyidir ancak derleyici her zaman hataları yakalar.  
  
## <a name="overloaded-methods"></a>Aşırı yüklenmiş yöntemler  
 Bir yöntem için parametrelerin farklı birleşimlerini sağlamak üzere kullanıcı denetiminizin izin vermek istiyorsanız, birden çok aşırı yükleme açık veri türleri kullanılarak yöntemi sağlar. Olarak bildirilen parametreleri oluşturmaktan kaçının `As Object` dahil olabilir herhangi bir veri türü olarak bu sınamada Yakalanacak değil hatalara neden olabilir.  
  
> [!NOTE]
>  Evrensel veri türü ortak dil çalışma zamanı `Object` yerine `Variant`. `Variant` dili kaldırıldı.  
  
 Örneğin, `Spin` bir kuramsal yöntemi `Widget` denetimi izin döndürme yön ve hız doğrudan belirtimi veya başka bir belirtim `Widget` hangi angular İtici Güç nesnesinden olan absorbed olacak:  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.
- [Olaylar](../../../../docs/standard/events/index.md)
- [Windows Forms Denetimlerindeki Özellikler](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)
