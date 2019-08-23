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
ms.openlocfilehash: 867bf97ea13654de6f9c0209c64b9320824f9665
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931746"
---
# <a name="method-implementation-in-custom-controls"></a>Özel Denetimlerde Yöntem Uygulama
Bir yöntem, bir denetime aynı şekilde, başka bir bileşende de uygulanacak şekilde uygulanır.  
  
 Visual Basic, bir yöntemin bir değer döndürmesi gerekiyorsa, olarak `Public Function`uygulanır. Değer döndürülmezse, bir `Public Sub`olarak uygulanır. Yöntemler aşağıdaki sözdizimi kullanılarak bildirilmiştir:  
  
```vb  
Public Function ConvertMatterToEnergy(Matter as Integer) As Integer  
   ' Conversion code goes here.  
End Function  
```  
  
 İşlevler bir değer döndürdüğü için, tamsayı, dize, nesne vb. gibi bir dönüş türü belirtmesi gerekir. Varsa bağımsız `Function` değişkenler `Sub` veya yordamlar de belirtilmelidir.  
  
 C#Visual Basic gibi işlevler ve yordamlar arasında ayrım yapmaz. Bir yöntem bir değer ya da döndürür `void`. Ortak bir C# yöntemi bildirmek için sözdizimi şöyledir:  
  
```csharp  
public int ConvertMatterToEnergy(int matter)  
{  
   // Conversion code goes here.  
}  
```  
  
 Bir yöntemi bildirdiğinizde, tüm bağımsız değişkenlerini mümkün olduğunda açık veri türleri olarak bildirin. Nesne başvurularını alan bağımsız değişkenler belirli sınıf türleri olarak bildirilmelidir — Örneğin, `As Widget` `As Object`yerine. Visual Basic, varsayılan ayar `Option Strict` otomatik olarak bu kuralı zorlar.  
  
 Yazılan bağımsız değişkenler, birçok geliştirici hatasının çalışma süresi yerine derleyici tarafından yakalanarak oluşmasına izin verir. Derleyici her zaman hataları yakalar, ancak çalışma zamanı testi yalnızca test paketi kadar iyidir.  
  
## <a name="overloaded-methods"></a>Aşırı yüklenmiş yöntemler  
 Denetiminizin kullanıcılarının bir yönteme farklı parametre bileşimleri sağlamasına izin vermek istiyorsanız, açık veri türleri kullanarak yönteminin birden çok aşırı yüklemesini sağlayın. Herhangi bir veri türü `As Object` içerebilen bir parametre oluşturmaktan kaçının. Bu, test sırasında yakalanmayan hatalara neden olabilir.  
  
> [!NOTE]
> Ortak dil çalışma zamanındaki `Object` evrensel veri türü `Variant`yerine. `Variant`dilden kaldırılmıştır.  
  
 Örneğin, `Spin` bir kuramsal `Widget` denetim yöntemi, doğrudan döndürme yönlerinin ve hızının belirtimindeki ya da angular itici güç 'in emin olduğu `Widget` başka bir nesnenin belirtimine izin verebilir:  
  
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

- [Olaylar](../../../standard/events/index.md)
- [Windows Forms Denetimlerindeki Özellikler](properties-in-windows-forms-controls.md)
