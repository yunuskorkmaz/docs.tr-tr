---
title: Visual Basic'de Erişim Düzeyleri
ms.date: 05/10/2018
helpviewer_keywords:
- members [Visual Basic], accessing in Visual Basic
- Friend access modifier
- access levels, declared elements
- access levels
- access modifiers
- Public access modifier
- Protected access modifier
- Protected Friend access modifier
- Private Protected access modifier
- Private access modifier
- declared elements [Visual Basic], access level
ms.assetid: 6e06c1ab-fd78-47f0-83a8-1152780b5e1a
ms.openlocfilehash: 1e2d43f33a352d3f4502965c5368eb901e7bffdf
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="access-levels-in-visual-basic"></a>Visual Basic'de Erişim Düzeyleri
*Erişim düzeyine* bildirilen öğesinin erişim olanağı kapsamını, başka bir deyişle, hangi kod onu okuma veya yazma izni yoktur. Bu, yalnızca öğe bildirme nasıl tarafından aynı zamanda öğenin kapsayıcı erişim düzeyine göre belirlenir. İçeren bir öğe erişemiyor kod herhangi bir kapsanan öğeleri erişemiyor, olanlar olarak bildirilen `Public`. Örneğin, bir `Public` değişkeni bir `Private` yapısı erişilebilir gelen yapısı içeren sınıf içinde değiştirebilir, ancak bu sınıfın dışında.  
  
## <a name="public"></a>Ortak  
 [Ortak](../../../../visual-basic/language-reference/modifiers/public.md) anahtar sözcüğü bildirimi deyiminde belirtir öğe aynı proje başka bir yerindeki kod projesine başvuru diğer projeler ve projesinden derleme erişilebilir. Aşağıdaki kod örneği gösterir `Public` bildirimi.  
  
```vb  
Public Class classForEverybody  
```  
  
 Kullanabileceğiniz `Public` yalnızca düzeyinde modül, arabirim veya ad alanı. Başka bir deyişle, bir kaynak dosya veya ad alanı, veya bir arabirim, modül, sınıf veya yapı içinde ancak bir yordam düzeyinde bir genel öğesi bildirebilirsiniz.  
  
## <a name="protected"></a>Korumalı  
 [Korumalı](../../../../visual-basic/language-reference/modifiers/protected.md) anahtar sözcüğü bildirimi deyiminde belirtir öğesi yalnızca aynı sınıfı içinde ya da bu sınıfından türetilen bir sınıftan erişilebilir olduğunu. Aşağıdaki kod örneği gösterir `Protected` bildirimi.  
  
```vb  
Protected Class classForMyHeirs  
```  
  
 Kullanabileceğiniz `Protected` yalnızca sınıfı düzeyde ve yalnızca zaman bildirdiğiniz bir sınıf üyesi. Başka bir deyişle, bir sınıf, ancak düzeyinde bir kaynak dosya veya ad alanı veya bir arabirim, modül, yapısı veya yordam içinde korumalı bir öğesi bildirebilirsiniz.  
  
## <a name="friend"></a>Arkadaş  
 [Arkadaş](../../../../visual-basic/language-reference/modifiers/friend.md) anahtar sözcüğü bildirimi deyiminde belirtir öğe aynı bütünleştirilmiş kod içinde değiştirebilir, ancak erişilebilir olduğunu derleme dışına. Aşağıdaki kod örneği gösterir `Friend` bildirimi.  
  
```vb  
Friend stringForThisProject As String  
```  
  
 Kullanabileceğiniz `Friend` yalnızca düzeyinde modül, arabirim veya ad alanı. Başka bir deyişle, bir kaynak dosya veya ad alanı, veya bir arabirim, modül, sınıf veya yapı içinde ancak bir yordam düzeyinde bir arkadaş öğesi bildirebilirsiniz.  
  
## <a name="protected-friend"></a>Korumalı Friend  
 `Protected` Ve `Friend` bildirimi deyiminde birlikte anahtar sözcükleri belirtin türetilen sınıflar ya da içinden öğe erişilebilen aynı bütünleştirilmiş kodda veya her ikisi de. Aşağıdaki kod örneği gösterir `Protected Friend` bildirimi.  
  
```vb  
Protected Friend stringForProjectAndHeirs As String  
```  
  
 Kullanabileceğiniz `Protected Friend` yalnızca sınıfı düzeyde ve yalnızca zaman bildirdiğiniz bir sınıf üyesi. Başka bir deyişle, bir sınıf, ancak düzeyinde bir kaynak dosya veya ad alanı veya bir arabirim, modül, yapısı veya yordam içinde korumalı friend öğesi bildirebilirsiniz.  
  
## <a name="private"></a>Özel  
 [Özel](../../../../visual-basic/language-reference/modifiers/private.md) anahtar sözcüğü bildirimi deyiminde belirtir öğesi yalnızca aynı modülü, sınıf veya yapı içinde erişilebilir olduğunu. Aşağıdaki kod örneği gösterir `Private` bildirimi.  
  
```vb  
Private numberForMeOnly As Integer  
```  
  
 Kullanabileceğiniz `Private` yalnızca modülü düzeyinde. Bu modül, sınıf veya yapı içinde ancak kaynak dosya veya ad alanı, bir arabirim içinde ya da bir yordamda düzeyinde özel bir öğesi bildirebilirsiniz anlamına gelir.  
  
 Modül düzeyinde `Dim` deyimi erişim düzeyi anahtar sözcüğü olmadan eşdeğer bir `Private` bildirimi. Ancak, kullanmak isteyebilirsiniz `Private` kodunuzu okumak ve yorumlamak daha kolay hale getirmek için anahtar sözcüğü.  

## <a name="private-protected"></a>Özel korumalı

[Özel korumalı](../../../language-reference/modifiers/private-protected.md) anahtar sözcüğü bildirimi deyiminde belirtir öğesi yalnızca aynı sınıfı içinde yanı sıra içeren sınıf ile aynı bütünleştirilmiş kodda bulunmadı türetilmiş sınıflarından erişilebildiğini. `Private Protected` Erişim değiştiricisi, Visual Basic 15,5 ile başlayarak desteklenir.

Aşağıdaki örnekte gösterildiği bir `Private Protected` bildirimi:

```vb
Private Protected internalValue As Integer
```

Bildirebilirsiniz bir `Private Protected` öğesi yalnızca bir sınıf içinde. Bir arabirim ya da yapısı içinde bildiremezsiniz veya bir kaynak dosya veya ad alanı, bir arabirim veya bir yapı içinde ya da bir yordamda düzeyinde bildirin.

`Private Protected` Erişim değiştiricisi Visual Basic 15,5 tarafından ve sonraki sürümlerinde desteklenir. Kullanmak için Visual Basic proje (*.vbproj) dosyasına aşağıdaki öğeyi ekleyin. Visual Basic 15,5 sürece veya üzeri, sisteminizde yüklü gibi Visual Basic derleyici en son sürümü tarafından desteklenen tüm dil özellikleri yararlanmanızı sağlar:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

Kullanılacak `Private Protected` erişim değiştiricisi, Visual Basic proje (*.vbproj) dosyanıza aşağıdaki öğeyi ekleyin:

```xml
<PropertyGroup>
   <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

 ## <a name="access-modifiers"></a>Erişim Değiştiricileri  
 Erişim düzeyi belirtin anahtar sözcükleri adlı *erişim değiştiricileri*. Aşağıdaki tabloda erişim değiştiricileri karşılaştırır.  
  
|Erişim değiştiricisi|Verilen erişim düzeyi|Bu erişim düzeyi ile bildirebilir öğeleri|Bildirim bağlam içinde bu değiştirici kullanabilirsiniz|  
|---------------------|--------------------------|-----------------------------------------------------|----------------------------------------------------------------|  
|`Public`|Kısıtlanmamış:<br /><br /> Bir genel öğesi görmek için herhangi bir kod erişim|Arabirimler<br /><br /> Modüller<br /><br /> Sınıflar<br /><br /> Yapılar<br /><br /> Yapı üyeleri<br /><br /> Yordamlar<br /><br /> Özellikler<br /><br /> Üye değişkenleri<br /><br /> Sabitler<br /><br /> Numaralandırmalar<br /><br /> Olaylar<br /><br /> Dış bildirimler<br /><br /> Temsilciler|Kaynak dosya<br /><br /> Ad Alanı<br /><br /> Arabirim<br /><br /> Modül<br /><br /> örneği<br /><br /> Yapı|  
|`Protected`|Derivational:<br /><br /> Korumalı bir öğe veya ondan, türetilmiş bir sınıf öğesi erişebilir bildirir sınıfında kod|Arabirimler<br /><br /> Sınıflar<br /><br /> Yapılar<br /><br /> Yordamlar<br /><br /> Özellikler<br /><br /> Üye değişkenleri<br /><br /> Sabitler<br /><br /> Numaralandırmalar<br /><br /> Olaylar<br /><br /> Dış bildirimler<br /><br /> Temsilciler|örneği|  
|`Friend`|Derleme:<br /><br /> Arkadaş öğesi erişebildiğinizi bildirir derlemede kod|Arabirimler<br /><br /> Modüller<br /><br /> Sınıflar<br /><br /> Yapılar<br /><br /> Yapı üyeleri<br /><br /> Yordamlar<br /><br /> Özellikler<br /><br /> Üye değişkenleri<br /><br /> Sabitler<br /><br /> Numaralandırmalar<br /><br /> Olaylar<br /><br /> Dış bildirimler<br /><br /> Temsilciler|Kaynak dosya<br /><br /> Ad Alanı<br /><br /> Arabirim<br /><br /> Modül<br /><br /> örneği<br /><br /> Yapı|  
|`Protected``Friend`|Birleşim, `Protected` ve `Friend`:<br /><br /> Aynı sınıfın veya bir korumalı friend öğe olarak veya öğenin sınıfından türetilen sınıf içinde aynı bütünleştirilmiş kod, erişilebilir|Arabirimler<br /><br /> Sınıflar<br /><br /> Yapılar<br /><br /> Yordamlar<br /><br /> Özellikler<br /><br /> Üye değişkenleri<br /><br /> Sabitler<br /><br /> Numaralandırmalar<br /><br /> Olaylar<br /><br /> Dış bildirimler<br /><br /> Temsilciler|örneği|  
|`Private`|Bildirim Bağlam:<br /><br /> Özel bir öğesi, içerdiği türler içinde dahil olmak üzere kod bildiren türü kodda öğe erişebilirsiniz|Arabirimler<br /><br /> Sınıflar<br /><br /> Yapılar<br /><br /> Yapı üyeleri<br /><br /> Yordamlar<br /><br /> Özellikler<br /><br /> Üye değişkenleri<br /><br /> Sabitler<br /><br /> Numaralandırmalar<br /><br /> Olaylar<br /><br /> Dış bildirimler<br /><br /> Temsilciler|Modül<br /><br /> örneği<br /><br /> Yapı|
|`Private Protected`|Özel bir korumalı öğesi bildirir sınıfı kodda veya bas sınıf ile aynı bütünleştirilmiş kodda bulunmadı türetilmiş bir sınıf kodu.|Arabirimler<br /><br /> Sınıflar<br /><br /> Yapılar<br /><br /> Yordamlar<br /><br /> Özellikler<br /><br /> Üye değişkenleri<br /><br /> Sabitler<br /><br /> Numaralandırmalar<br /><br /> Olaylar<br /><br /> Dış bildirimler<br /><br /> Temsilciler|örneği|
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dim Deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Static](../../../../visual-basic/language-reference/modifiers/static.md)  
 [Bildirilen Öğe Adları](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Bildirilmiş Öğelere Başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Bildirilen Öğe Özellikleri](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [Visual Basic'de ömür](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Visual Basic'de kapsam](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [Nasıl yapılır: Bir Değişkenin Kullanılabilirliğini Denetleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md)  
 [Değişkenler](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
