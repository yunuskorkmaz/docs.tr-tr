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
ms.openlocfilehash: d8f2f16d2fb15f2e840f13f177d3fea83fda315e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843108"
---
# <a name="access-levels-in-visual-basic"></a>Visual Basic'de Erişim Düzeyleri
*Erişim düzeyi* bildirilen bir öğenin erişim olanağı kapsamını, başka bir deyişle, hangi kod dosyayı okuma veya yazma izni yoktur. Bu, yalnızca öğenin kendisinin nasıl bildirdiğiniz tarafından aynı zamanda öğenin kapsayıcı erişim düzeyine göre belirlenir. Bir kapsayıcı öğe erişemiyor kod herhangi birini kendi içerilen öğelerin erişemez, bile olarak bildirilen `Public`. Örneğin, bir `Public` değişkeninde bir `Private` yapısı erişilebilir değil, ancak yapı içeren bir sınıf içinde o sınıf dışında.  
  
## <a name="public"></a>Ortak  
 [Genel](../../../../visual-basic/language-reference/modifiers/public.md) bildirim deyimindeki bir anahtar sözcük belirtir öğesi aynı projede herhangi bir kod projesi başvuran diğer projeler ve projeden oluşturulan herhangi bir derleme erişilebilir. Aşağıdaki kod, bir örneği gösterilmektedir. `Public` bildirimi.  
  
```vb  
Public Class classForEverybody  
```  
  
 Kullanabileceğiniz `Public` yalnızca düzeyinde modülü, arabirim veya ad alanı. Başka bir deyişle, bir kaynak dosya veya ad alanı veya arabirimi, modül, sınıf veya yapı içinde ancak bir yordamda düzeyde bir genel öğesi bildirebilirsiniz.  
  
## <a name="protected"></a>Korumalı  
 [Korumalı](../../../../visual-basic/language-reference/modifiers/protected.md) anahtar sözcüğü bir bildirim deyiminde öğesi yalnızca aynı sınıf içinde veya bu sınıftan türetilen bir sınıftan erişilebilir olduğunu belirtir. Aşağıdaki kod, bir örneği gösterilmektedir. `Protected` bildirimi.  
  
```vb  
Protected Class classForMyHeirs  
```  
  
 Kullanabileceğiniz `Protected` yalnızca sınıf düzeyinde ve yalnızca bildirdiğinizde sınıfının bir üyesi. Başka bir deyişle, bir sınıf, ancak düzeyinde bir kaynak dosya veya ad alanı veya arabirimi, modül, yapı veya yordam içinde korumalı bir öğe bildirebilirsiniz.  
  
## <a name="friend"></a>Arkadaş  
 [Arkadaş](../../../../visual-basic/language-reference/modifiers/friend.md) bildirim deyimindeki bir anahtar sözcük belirtir öğesi değil, ancak aynı bütünleştirilmiş kod içinde erişilebilir olduğunu derleme dışından. Aşağıdaki kod, bir örneği gösterilmektedir. `Friend` bildirimi.  
  
```vb  
Friend stringForThisProject As String  
```  
  
 Kullanabileceğiniz `Friend` yalnızca düzeyinde modülü, arabirim veya ad alanı. Başka bir deyişle, bir arkadaş öğesi bir kaynak dosya veya ad alanı veya arabirimi, modül, sınıf veya yapı içinde ancak bir yordamda düzeyinde bildirebilirsiniz.  
  
## <a name="protected-friend"></a>Korumalı Friend  
 [Protected Friend](../../../language-reference/modifiers/protected-friend.md) anahtar sözcüğü birleşimi bildirim deyiminde belirtir öğesi veya türetilmiş sınıf içinden erişilebilir aynı derleme veya her ikisini de. Aşağıdaki kod, bir örneği gösterilmektedir. `Protected Friend` bildirimi.  
  
```vb  
Protected Friend stringForProjectAndHeirs As String  
```  
  
 Kullanabileceğiniz `Protected Friend` yalnızca sınıf düzeyinde ve yalnızca bildirdiğinizde sınıfının bir üyesi. Başka bir deyişle, bir sınıf, ancak düzeyinde bir kaynak dosya veya ad alanı veya arabirimi, modül, yapı veya yordam içinde bir korumalı friend öğesi bildirebilirsiniz.  
  
## <a name="private"></a>Özel  
 [Özel](../../../../visual-basic/language-reference/modifiers/private.md) anahtar sözcüğü bir bildirim deyiminde öğesi yalnızca aynı modül, sınıf veya yapı içinde erişilebilir olduğunu belirtir. Aşağıdaki kod, bir örneği gösterilmektedir. `Private` bildirimi.  
  
```vb  
Private numberForMeOnly As Integer  
```  
  
 Kullanabileceğiniz `Private` yalnızca Modül düzeyinde. Başka bir deyişle, bir modül, sınıf veya yapı içinde ancak bir kaynak dosya veya ad alanı, bir arabirim içinde veya bir yordamda düzeyinde özel bir öğeyi bildirebilirsiniz.  
  
 Modül düzeyinde `Dim` deyimi herhangi bir erişim düzeyi anahtar olmadan, bir `Private` bildirimi. Ancak, kullanmak isteyebilirsiniz `Private` kodunuzu okumak ve yorumlamak kolay hale getirmek için anahtar sözcüğü.  

## <a name="private-protected"></a>Özel korumalı

[Protected Private](../../../language-reference/modifiers/private-protected.md) anahtar sözcüğü birleşimi bildirim deyiminde öğesi yalnızca aynı sınıf içinde yanı sıra aynı bütünleştirilmiş kod içeren sınıf bulunan türetilmiş sınıflardan erişilebilir olduğunu belirtir. `Private Protected` Erişim değiştiricisi, Visual Basic 15.5 ile'den başlayarak desteklenir.

Aşağıdaki örnekte gösterildiği bir `Private Protected` bildirimi:

```vb
Private Protected internalValue As Integer
```

Bildirebilirsiniz bir `Private Protected` öğe yalnızca bir sınıf içinde. Bir arabirim ya da yapısı bildiremezsiniz ya da bir kaynak dosya veya ad alanı, bir arabirim veya bir yapı içinde veya bir yordamda düzeyinde bildirebilirsiniz.

`Private Protected` Erişim değiştiricisi, Visual Basic 15.5 ve sonraki sürümlerinde desteklenir. Bunu kullanmak için Visual Basic proje (*.vbproj) dosyanıza aşağıdaki öğeyi ekleyin. Sisteminizde sürece Visual Basic 15.5 veya üzeri yüklü olduğu, en son sürümü Visual Basic derleyicisi tarafından desteklenen dil özellikleri yararlanmanızı sağlar:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

Kullanılacak `Private Protected` erişim değiştiricisi, Visual Basic (*.vbproj) proje dosyanıza şu öğeyi ekleyin:

```xml
<PropertyGroup>
   <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

Daha fazla bilgi için [Visual Basic dil sürümü ayarını](../../../language-reference/configure-language-version.md).

## <a name="access-modifiers"></a>Erişim Değiştiricileri  

Erişim düzeyini sağlayacaklarını anahtar sözcükleri adlı *erişim değiştiricilerine*. Aşağıdaki tabloda, erişim değiştiricileri karşılaştırır.  
  
|Erişim değiştiricisi|Verilen erişim düzeyi|Öğeleri bu erişim düzeyiyle bildirebilirsiniz.|Bu değiştirici, içinde kullanabileceğiniz bildirimi bağlamı|  
|---------------------|--------------------------|-----------------------------------------------------|----------------------------------------------------------------|  
|`Public`|Sınırsız:<br /><br /> Genel öğesinin herhangi bir kod erişimi|Arabirimler<br /><br /> Modüller<br /><br /> Sınıflar<br /><br /> Yapılar<br /><br /> Yapı üyeleri<br /><br /> Yordamlar<br /><br /> Özellikler<br /><br /> Üye değişkenleri<br /><br /> Sabitler<br /><br /> Numaralandırmalar<br /><br /> Olaylar<br /><br /> Dış bildirimler<br /><br /> Temsilciler|Kaynak dosyası<br /><br /> Ad Alanı<br /><br /> Arabirim<br /><br /> Modül<br /><br /> örneği<br /><br /> Yapı|  
|`Protected`|Derivational:<br /><br /> Korumalı bir öğe veya bu türden türetilmiş bir sınıf öğesi erişip bildirir sınıfında kod|Arabirimler<br /><br /> Sınıflar<br /><br /> Yapılar<br /><br /> Yordamlar<br /><br /> Özellikler<br /><br /> Üye değişkenleri<br /><br /> Sabitler<br /><br /> Numaralandırmalar<br /><br /> Olaylar<br /><br /> Dış bildirimler<br /><br /> Temsilciler|örneği|  
|`Friend`|Derleme:<br /><br /> Arkadaş öğesi erişebileceğini bildiren derlemede kod|Arabirimler<br /><br /> Modüller<br /><br /> Sınıflar<br /><br /> Yapılar<br /><br /> Yapı üyeleri<br /><br /> Yordamlar<br /><br /> Özellikler<br /><br /> Üye değişkenleri<br /><br /> Sabitler<br /><br /> Numaralandırmalar<br /><br /> Olaylar<br /><br /> Dış bildirimler<br /><br /> Temsilciler|Kaynak dosyası<br /><br /> Ad Alanı<br /><br /> Arabirim<br /><br /> Modül<br /><br /> örneği<br /><br /> Yapı|  
|`Protected``Friend`|Birleşim, `Protected` ve `Friend`:<br /><br /> Aynı sınıf ya da korumalı friend öğesi olarak ya da öğenin sınıfından türetilen herhangi bir sınıf içinde aynı bütünleştirilmiş kod, buna erişebilir|Arabirimler<br /><br /> Sınıflar<br /><br /> Yapılar<br /><br /> Yordamlar<br /><br /> Özellikler<br /><br /> Üye değişkenleri<br /><br /> Sabitler<br /><br /> Numaralandırmalar<br /><br /> Olaylar<br /><br /> Dış bildirimler<br /><br /> Temsilciler|örneği|  
|`Private`|Bildirim içeriği:<br /><br /> Kod içinde kapsanan türleri dahil olmak üzere özel bir öğe, öğe erişip bildiren türü kodu|Arabirimler<br /><br /> Sınıflar<br /><br /> Yapılar<br /><br /> Yapı üyeleri<br /><br /> Yordamlar<br /><br /> Özellikler<br /><br /> Üye değişkenleri<br /><br /> Sabitler<br /><br /> Numaralandırmalar<br /><br /> Olaylar<br /><br /> Dış bildirimler<br /><br /> Temsilciler|Modül<br /><br /> örneği<br /><br /> Yapı|
|`Private Protected`|Özel bir korumalı öğe bildirir bir sınıftaki kod veya bas sınıf olarak aynı derlemede bulunan türetilmiş bir sınıf içinde kod.|Arabirimler<br /><br /> Sınıflar<br /><br /> Yapılar<br /><br /> Yordamlar<br /><br /> Özellikler<br /><br /> Üye değişkenleri<br /><br /> Sabitler<br /><br /> Numaralandırmalar<br /><br /> Olaylar<br /><br /> Dış bildirimler<br /><br /> Temsilciler|örneği|
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dim Deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Static](../../../../visual-basic/language-reference/modifiers/static.md)
- [Bildirilen Öğe Adları](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Bildirilmiş Öğelere Başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Bildirilen Öğe Özellikleri](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [Visual Basic'de ömür](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Visual Basic'de kapsam](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Nasıl yapılır: Bir değişkenin kullanılabilirliğini denetleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md)
- [Değişkenler](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
