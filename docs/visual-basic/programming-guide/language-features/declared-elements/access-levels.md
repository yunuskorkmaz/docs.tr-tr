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
ms.openlocfilehash: d1548f7850c68bc3c5422cf9d8d3d30eaa4aa8f3
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73035881"
---
# <a name="access-levels-in-visual-basic"></a>Visual Basic'de Erişim Düzeyleri

Tanımlı bir öğenin *erişim düzeyi* buna erişim yeteneğinin, diğer bir deyişle, hangi kodun bu dosyayı okuma veya yazma iznine sahip olduğu bir şeydir. Bu, yalnızca öğenin kendisini nasıl tanımlayacağınızın yanı sıra öğenin kapsayıcısının erişim düzeyiyle de belirlenir. Kapsayan bir öğeye erişememiş kod, `Public`olarak bildirilenler bile içerilen öğelerinden hiçbirine erişemez. Örneğin, bir `Private` yapısındaki `Public` değişkenine, yapıyı içeren sınıfın içinden, ancak bu sınıfın dışından erişilebilir.

## <a name="public"></a>Ortak

Bildirim deyimindeki [Public](../../../language-reference/modifiers/public.md) anahtar sözcüğü, öğeye aynı projede herhangi bir yerde, projeye başvuran diğer projelerden ve projeden oluşturulan herhangi bir derlemeden erişilebileceğini belirtir. Aşağıdaki kod bir örnek `Public` bildirimi gösterir:

```vb
Public Class ClassForEverybody
```

`Public` yalnızca modül, arabirim veya ad alanı düzeyinde kullanabilirsiniz. Bu, bir genel öğeyi bir kaynak dosya veya ad alanı düzeyinde ya da bir arabirim, modül, sınıf ya da yapı içinde veya bir yordamda değil, bir şekilde bildirebilmeniz anlamına gelir.
  
## <a name="protected"></a>Korumalı

Bildirim deyimindeki [Protected](../../../language-reference/modifiers/protected.md) anahtar sözcüğü, öğesinin yalnızca aynı sınıftan veya bu sınıftan türetilmiş bir sınıftan erişilebilir olduğunu belirtir. Aşağıdaki kod bir örnek `Protected` bildirimi gösterir:

```vb
Protected Class ClassForMyHeirs
```

`Protected` yalnızca sınıf düzeyinde ve yalnızca bir sınıfın bir üyesini bildirdiğinizde kullanabilirsiniz. Bu, bir kaynak dosya veya ad alanı düzeyinde ya da bir arabirim, modül, yapı veya yordamın içinde değil, bir sınıfta korunan bir öğe bildirebilmeniz anlamına gelir.

## <a name="friend"></a>Arkadaş

Bildirim deyimindeki [Friend](../../../language-reference/modifiers/friend.md) anahtar sözcüğü, öğesine aynı derleme içinden erişilemeyeceğini, ancak derlemenin dışından erişilebileceğini belirtir. Aşağıdaki kod bir örnek `Friend` bildirimi gösterir:

```vb
Friend stringForThisProject As String
```

`Friend` yalnızca modül, arabirim veya ad alanı düzeyinde kullanabilirsiniz. Bu, bir kaynak dosya veya ad alanı düzeyinde ya da bir arabirim, modül, sınıf ya da yapının içinde veya bir yordamda değil, bir arkadaş öğesi bildirebilmeniz anlamına gelir.

## <a name="protected-friend"></a>Protected Friend

Bildirim deyimindeki [Protected Friend](../../../language-reference/modifiers/protected-friend.md) anahtar sözcüğü birleşimi, öğesine türetilmiş sınıflardan veya aynı derlemenin içinden ya da her ikisinin de erişilebileceğini belirtir. Aşağıdaki kod bir örnek `Protected Friend` bildirimi gösterir:

```vb
Protected Friend stringForProjectAndHeirs As String
```

`Protected Friend` yalnızca sınıf düzeyinde ve yalnızca bir sınıfın bir üyesini bildirdiğinizde kullanabilirsiniz. Bu, bir kaynak dosya veya ad alanı düzeyinde ya da bir arabirim, modül, yapı veya yordamın içinde değil, bir sınıfta korunan bir arkadaş öğesi bildirebilmeniz anlamına gelir.

## <a name="private"></a>Özel

Bildirim deyimindeki [Private](../../../language-reference/modifiers/private.md) anahtar sözcüğü, öğeye yalnızca aynı modül, sınıf veya yapı içinden erişilebileceğini belirtir. Aşağıdaki kod bir örnek `Private` bildirimi gösterir:

```vb
Private _numberForMeOnly As Integer
```

Yalnızca modül düzeyinde `Private` kullanabilirsiniz. Bu, bir özel öğeyi bir modül, sınıf veya yapı içinde, bir kaynak dosya veya ad alanı düzeyinde, bir arabirim içinde veya bir yordamda bildirebilmeniz anlamına gelir.

Modül düzeyinde, erişim düzeyi anahtar sözcükleri olmayan `Dim` deyimleri `Private` bildirimine eşdeğerdir. Ancak, kodunuzun okunmasını ve yorumlanması daha kolay hale getirmek için `Private` anahtar sözcüğünü kullanmak isteyebilirsiniz.

## <a name="private-protected"></a>Private Protected

Bildirim deyimindeki [özel korumalı](../../../language-reference/modifiers/private-protected.md) anahtar sözcük birleşimi, öğesinin yalnızca aynı sınıftan erişilebilir ve aynı derlemede bulunan türetilmiş sınıflardan ve kapsayan sınıfla erişilebilir olduğunu belirtir. `Private Protected` erişim değiştiricisi Visual Basic 15,5 ' den başlayarak desteklenir.

Aşağıdaki örnek bir `Private Protected` bildirimi gösterir:

```vb
Private Protected internalValue As Integer
```

Yalnızca bir sınıfın içinde bir `Private Protected` öğesi bildirebilirsiniz. Bunu bir arabirim veya yapı içinde bildiremezsiniz veya bir arabirim ya da bir yapı içinde ya da bir yordamda bir kaynak dosya veya ad alanı düzeyinde bildiremezsiniz.

`Private Protected` erişim değiştiricisi Visual Basic 15,5 ve üzeri tarafından desteklenir. Bunu kullanmak için, Visual Basic projesi ( *\*. vbproj*) dosyanıza aşağıdaki öğeyi ekleyin. Visual Basic 15,5 veya üzeri bir sürümü sisteminize yüklendiği sürece, Visual Basic derleyicinin en son sürümü tarafından desteklenen tüm dil özelliklerinden yararlanmanızı sağlar:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

`Private Protected` erişim değiştiricisini kullanmak için, aşağıdaki öğeyi Visual Basic projesi ( *\*. vbproj*) dosyanıza eklemeniz gerekir:

```xml
<PropertyGroup>
   <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

Daha fazla bilgi için bkz. [Visual Basic dil sürümünü ayarlama](../../../language-reference/configure-language-version.md).

## <a name="access-modifiers"></a>Erişim Değiştiricileri

Erişim düzeyi belirten anahtar sözcüklere *erişim değiştiricileri*denir. Aşağıdaki tabloda erişim değiştiricileri karşılaştırılmaktadır:

|Erişim değiştiricisi|Erişim düzeyi verildi|Bu erişim düzeyiyle bildirebileceğiniz öğeler|Bu değiştiriciyi kullanabileceğiniz bildirim bağlamı|
|---------------------|--------------------------|-----------------------------------------------------|----------------------------------------------------------------|
|`Public`|Edin<br /><br /> Ortak bir öğeyi görebileceğiniz herhangi bir kod, buna erişebilir|Arabirimler<br /><br /> Modüller<br /><br /> Sınıflar<br /><br /> Yapılar<br /><br /> Yapı üyeleri<br /><br /> Yordamlar<br /><br /> Özellikler<br /><br /> Üye değişkenleri<br /><br /> Sabitler<br /><br /> Numaralandırmalar<br /><br /> Olaylar<br /><br /> Dış bildirimler<br /><br /> Temsilciler|Kaynak dosya<br /><br /> Ad Alanı<br /><br /> Arabirim<br /><br /> Modül<br /><br /> örneği<br /><br /> Yapı|
|`Protected`|Türetme:<br /><br /> Bir korumalı öğeyi veya ondan türetilmiş bir sınıfı bildiren sınıftaki kod öğeye erişebilir|Arabirimler<br /><br /> Sınıflar<br /><br /> Yapılar<br /><br /> Yordamlar<br /><br /> Özellikler<br /><br /> Üye değişkenleri<br /><br /> Sabitler<br /><br /> Numaralandırmalar<br /><br /> Olaylar<br /><br /> Dış bildirimler<br /><br /> Temsilciler|örneği|
|`Friend`|Derleme:<br /><br /> Bir Friend öğesini bildiren derlemede bulunan kod, buna erişebilir|Arabirimler<br /><br /> Modüller<br /><br /> Sınıflar<br /><br /> Yapılar<br /><br /> Yapı üyeleri<br /><br /> Yordamlar<br /><br /> Özellikler<br /><br /> Üye değişkenleri<br /><br /> Sabitler<br /><br /> Numaralandırmalar<br /><br /> Olaylar<br /><br /> Dış bildirimler<br /><br /> Temsilciler|Kaynak dosya<br /><br /> Ad Alanı<br /><br /> Arabirim<br /><br /> Modül<br /><br /> örneği<br /><br /> Yapı|
|`Protected``Friend`|`Protected` ve `Friend`birleşimi:<br /><br /> Aynı sınıftaki veya korunan arkadaş öğesiyle aynı derlemede bulunan veya öğenin sınıfından türetilmiş herhangi bir sınıfın içindeki kod, buna erişebilir|Arabirimler<br /><br /> Sınıflar<br /><br /> Yapılar<br /><br /> Yordamlar<br /><br /> Özellikler<br /><br /> Üye değişkenleri<br /><br /> Sabitler<br /><br /> Numaralandırmalar<br /><br /> Olaylar<br /><br /> Dış bildirimler<br /><br /> Temsilciler|örneği|
|`Private`|Bildirim bağlamı:<br /><br /> İçerilen türler içindeki kod dahil olmak üzere özel bir öğeyi bildiren türdeki kod öğeye erişebilir|Arabirimler<br /><br /> Sınıflar<br /><br /> Yapılar<br /><br /> Yapı üyeleri<br /><br /> Yordamlar<br /><br /> Özellikler<br /><br /> Üye değişkenleri<br /><br /> Sabitler<br /><br /> Numaralandırmalar<br /><br /> Olaylar<br /><br /> Dış bildirimler<br /><br /> Temsilciler|Modül<br /><br /> örneği<br /><br /> Yapı|
|`Private Protected`|Sınıf içindeki özel korumalı öğeyi bildiren kod veya aynı derlemede bulunan türetilmiş bir sınıftaki kodu, bas sınıfıyla aynı derlemede bulabilirsiniz.|Arabirimler<br /><br /> Sınıflar<br /><br /> Yapılar<br /><br /> Yordamlar<br /><br /> Özellikler<br /><br /> Üye değişkenleri<br /><br /> Sabitler<br /><br /> Numaralandırmalar<br /><br /> Olaylar<br /><br /> Dış bildirimler<br /><br /> Temsilciler|örneği|

## <a name="see-also"></a>Ayrıca bkz.

- [Dim Deyimi](../../../language-reference/statements/dim-statement.md)
- [Static](../../../language-reference/modifiers/static.md)
- [Bildirilen Öğe Adları](declared-element-names.md)
- [Bildirilmiş Öğelere Başvurular](references-to-declared-elements.md)
- [Bildirilen Öğe Özellikleri](declared-element-characteristics.md)
- [Visual Basic ömrü](lifetime.md)
- [Visual Basic kapsam](scope.md)
- [Nasıl yapılır: Bir Değişkenin Kullanılabilirliğini Denetleme](how-to-control-the-availability-of-a-variable.md)
- [Değişkenler](../variables/index.md)
- [Değişken Bildirimi](../variables/variable-declaration.md)
