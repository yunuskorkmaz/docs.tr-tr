---
description: 'Hakkında daha fazla bilgi edinin: Visual Basic erişim düzeyleri'
title: Erişim Düzeyleri
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
ms.openlocfilehash: bd26dce5490fde915aeef0a1293ee504a9d4984c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100464748"
---
# <a name="access-levels-in-visual-basic"></a>Visual Basic'de Erişim Düzeyleri

Tanımlı bir öğenin *erişim düzeyi* buna erişim yeteneğinin, diğer bir deyişle, hangi kodun bu dosyayı okuma veya yazma iznine sahip olduğu bir şeydir. Bu, yalnızca öğenin kendisini nasıl tanımlayacağınızın yanı sıra öğenin kapsayıcısının erişim düzeyiyle de belirlenir. Kapsayan bir öğeye erişememiş kod, olarak da tanımlananlar dahil olmak üzere içerilen öğelerinden hiçbirine erişemez `Public` . Örneğin, `Public` bir yapıda bir değişkene, `Private` yapıyı içeren sınıfın içinden erişilebilir, ancak bu sınıfın dışından erişilemez.

## <a name="public"></a>Genel

Bildirim deyimindeki [Public](../../../language-reference/modifiers/public.md) anahtar sözcüğü, öğeye aynı projede herhangi bir yerde, projeye başvuran diğer projelerden ve projeden oluşturulan herhangi bir derlemeden erişilebileceğini belirtir. Aşağıdaki kod bir örnek bildirimi gösterir `Public` :

```vb
Public Class ClassForEverybody
```

`Public`Yalnızca modül, arabirim veya ad alanı düzeyinde kullanabilirsiniz. Bu, bir genel öğeyi bir kaynak dosya veya ad alanı düzeyinde ya da bir arabirim, modül, sınıf ya da yapı içinde veya bir yordamda değil, bir şekilde bildirebilmeniz anlamına gelir.
  
## <a name="protected"></a>Korumalı

Bildirim deyimindeki [Protected](../../../language-reference/modifiers/protected.md) anahtar sözcüğü, öğesinin yalnızca aynı sınıftan veya bu sınıftan türetilmiş bir sınıftan erişilebilir olduğunu belirtir. Aşağıdaki kod bir örnek bildirimi gösterir `Protected` :

```vb
Protected Class ClassForMyHeirs
```

`Protected`Yalnızca sınıf düzeyinde ve yalnızca bir sınıfın üyesini bildirdiğinizde kullanabilirsiniz. Bu, bir kaynak dosya veya ad alanı düzeyinde ya da bir arabirim, modül, yapı veya yordamın içinde değil, bir sınıfta korunan bir öğe bildirebilmeniz anlamına gelir.

## <a name="friend"></a>Arkadaş

Bildirim deyimindeki [Friend](../../../language-reference/modifiers/friend.md) anahtar sözcüğü, öğesine aynı derleme içinden erişilemeyeceğini, ancak derlemenin dışından erişilebileceğini belirtir. Aşağıdaki kod bir örnek bildirimi gösterir `Friend` :

```vb
Friend stringForThisProject As String
```

`Friend`Yalnızca modül, arabirim veya ad alanı düzeyinde kullanabilirsiniz. Bu, bir kaynak dosya veya ad alanı düzeyinde ya da bir arabirim, modül, sınıf ya da yapının içinde veya bir yordamda değil, bir arkadaş öğesi bildirebilmeniz anlamına gelir.

## <a name="protected-friend"></a>Protected Friend

Bildirim deyimindeki [Protected Friend](../../../language-reference/modifiers/protected-friend.md) anahtar sözcüğü birleşimi, öğesine türetilmiş sınıflardan veya aynı derlemenin içinden ya da her ikisinin de erişilebileceğini belirtir. Aşağıdaki kod bir örnek bildirimi gösterir `Protected Friend` :

```vb
Protected Friend stringForProjectAndHeirs As String
```

`Protected Friend`Yalnızca sınıf düzeyinde ve yalnızca bir sınıfın üyesini bildirdiğinizde kullanabilirsiniz. Bu, bir kaynak dosya veya ad alanı düzeyinde ya da bir arabirim, modül, yapı veya yordamın içinde değil, bir sınıfta korunan bir arkadaş öğesi bildirebilmeniz anlamına gelir.

## <a name="private"></a>Özel

Bildirim deyimindeki [Private](../../../language-reference/modifiers/private.md) anahtar sözcüğü, öğeye yalnızca aynı modül, sınıf veya yapı içinden erişilebileceğini belirtir. Aşağıdaki kod bir örnek bildirimi gösterir `Private` :

```vb
Private _numberForMeOnly As Integer
```

`Private`Yalnızca modül düzeyinde kullanabilirsiniz. Bu, bir özel öğeyi bir modül, sınıf veya yapı içinde, bir kaynak dosya veya ad alanı düzeyinde, bir arabirim içinde veya bir yordamda bildirebilmeniz anlamına gelir.

Modül düzeyinde, `Dim` herhangi bir erişim düzeyi anahtar sözcüğü olmayan ifade bir `Private` bildirime eşdeğerdir. Bununla birlikte, `Private` kodunuzun okunmasını ve yorumlanması daha kolay hale getirmek için anahtar sözcüğünü kullanmak isteyebilirsiniz.

## <a name="private-protected"></a>Private Protected

Bildirim deyimindeki [özel korumalı](../../../language-reference/modifiers/private-protected.md) anahtar sözcük birleşimi, öğesinin yalnızca aynı sınıftan erişilebilir ve aynı derlemede bulunan türetilmiş sınıflardan ve kapsayan sınıfla erişilebilir olduğunu belirtir. `Private Protected`Erişim değiştiricisi Visual Basic 15,5 ' den başlayarak desteklenir.

Aşağıdaki örnekte bir bildirim gösterilmektedir `Private Protected` :

```vb
Private Protected internalValue As Integer
```

`Private Protected`Yalnızca bir sınıfın içinde bir öğe bildirebilirsiniz. Bunu bir arabirim veya yapı içinde bildiremezsiniz veya bir arabirim ya da bir yapı içinde ya da bir yordamda bir kaynak dosya veya ad alanı düzeyinde bildiremezsiniz.

`Private Protected`Erişim değiştiricisi Visual Basic 15,5 ve üzeri sürümlerde desteklenir. Bunu kullanmak için, Visual Basic projesi (*\* . vbproj*) dosyanıza aşağıdaki öğeyi ekleyin. Visual Basic 15,5 veya üzeri bir sürümü sisteminize yüklendiği sürece, Visual Basic derleyicinin en son sürümü tarafından desteklenen tüm dil özelliklerinden yararlanmanızı sağlar:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

`Private Protected`Erişim değiştiricisini kullanmak için, Visual Basic projesi (*\* . vbproj*) dosyanıza aşağıdaki öğeyi eklemeniz gerekir:

```xml
<PropertyGroup>
   <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

Daha fazla bilgi için bkz. [Visual Basic dil sürümünü ayarlama](../../../language-reference/configure-language-version.md).

## <a name="access-modifiers"></a>Erişim Değiştiricileri

Erişim düzeyi belirten anahtar sözcüklere *erişim değiştiricileri* denir. Aşağıdaki tabloda erişim değiştiricileri karşılaştırılmaktadır:

|Erişim değiştiricisi|Erişim düzeyi verildi|Bu erişim düzeyiyle bildirebileceğiniz öğeler|Bu değiştiriciyi kullanabileceğiniz bildirim bağlamı|
|---------------------|--------------------------|-----------------------------------------------------|----------------------------------------------------------------|
|`Public`|Edin<br /><br /> Ortak bir öğeyi görebileceğiniz herhangi bir kod, buna erişebilir|Arabirimler<br /><br /> Modül<br /><br /> Sınıflar<br /><br /> Yapılar<br /><br /> Yapı üyeleri<br /><br /> Yordamlar<br /><br /> Özellikler<br /><br /> Üye değişkenleri<br /><br /> Sabitler<br /><br /> Listelemeler<br /><br /> Ekinlikler<br /><br /> Dış bildirimler<br /><br /> Temsilciler|Kaynak dosya<br /><br /> Ad Alanı<br /><br /> Arabirim<br /><br /> Modül<br /><br /> Sınıf<br /><br /> Yapı|
|`Protected`|Türetme:<br /><br /> Bir korumalı öğeyi veya ondan türetilmiş bir sınıfı bildiren sınıftaki kod öğeye erişebilir|Arabirimler<br /><br /> Sınıflar<br /><br /> Yapılar<br /><br /> Yordamlar<br /><br /> Özellikler<br /><br /> Üye değişkenleri<br /><br /> Sabitler<br /><br /> Listelemeler<br /><br /> Ekinlikler<br /><br /> Dış bildirimler<br /><br /> Temsilciler|Sınıf|
|`Friend`|Derleme:<br /><br /> Bir Friend öğesini bildiren derlemede bulunan kod, buna erişebilir|Arabirimler<br /><br /> Modül<br /><br /> Sınıflar<br /><br /> Yapılar<br /><br /> Yapı üyeleri<br /><br /> Yordamlar<br /><br /> Özellikler<br /><br /> Üye değişkenleri<br /><br /> Sabitler<br /><br /> Listelemeler<br /><br /> Ekinlikler<br /><br /> Dış bildirimler<br /><br /> Temsilciler|Kaynak dosya<br /><br /> Ad Alanı<br /><br /> Arabirim<br /><br /> Modül<br /><br /> Sınıf<br /><br /> Yapı|
|`Protected` `Friend`|Ve birleşimi `Protected` `Friend` :<br /><br /> Aynı sınıftaki veya korunan arkadaş öğesiyle aynı derlemede bulunan veya öğenin sınıfından türetilmiş herhangi bir sınıfın içindeki kod, buna erişebilir|Arabirimler<br /><br /> Sınıflar<br /><br /> Yapılar<br /><br /> Yordamlar<br /><br /> Özellikler<br /><br /> Üye değişkenleri<br /><br /> Sabitler<br /><br /> Listelemeler<br /><br /> Ekinlikler<br /><br /> Dış bildirimler<br /><br /> Temsilciler|Sınıf|
|`Private`|Bildirim bağlamı:<br /><br /> İçerilen türler içindeki kod dahil olmak üzere özel bir öğeyi bildiren türdeki kod öğeye erişebilir|Arabirimler<br /><br /> Sınıflar<br /><br /> Yapılar<br /><br /> Yapı üyeleri<br /><br /> Yordamlar<br /><br /> Özellikler<br /><br /> Üye değişkenleri<br /><br /> Sabitler<br /><br /> Listelemeler<br /><br /> Ekinlikler<br /><br /> Dış bildirimler<br /><br /> Temsilciler|Modül<br /><br /> Sınıf<br /><br /> Yapı|
|`Private Protected`|Sınıf içindeki özel korumalı öğeyi bildiren kod veya aynı derlemede bulunan türetilmiş bir sınıftaki kodu, bas sınıfıyla aynı derlemede bulabilirsiniz.|Arabirimler<br /><br /> Sınıflar<br /><br /> Yapılar<br /><br /> Yordamlar<br /><br /> Özellikler<br /><br /> Üye değişkenleri<br /><br /> Sabitler<br /><br /> Listelemeler<br /><br /> Ekinlikler<br /><br /> Dış bildirimler<br /><br /> Temsilciler|Sınıf|

## <a name="see-also"></a>Ayrıca bkz.

- [Dim Deyimi](../../../language-reference/statements/dim-statement.md)
- [Static](../../../language-reference/modifiers/static.md)
- [Bildirilen Öğe Adları](declared-element-names.md)
- [Bildirilmiş Öğelere Başvurular](references-to-declared-elements.md)
- [Bildirilen Öğe Özellikleri](declared-element-characteristics.md)
- [Visual Basic'de Ömür](lifetime.md)
- [Visual Basic'de Kapsam](scope.md)
- [Nasıl yapılır: Bir Değişkenin Kullanılabilirliğini Denetleme](how-to-control-the-availability-of-a-variable.md)
- [Değişkenler](../variables/index.md)
- [Değişken Bildirimi](../variables/variable-declaration.md)
