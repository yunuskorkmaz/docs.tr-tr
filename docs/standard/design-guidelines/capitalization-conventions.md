---
title: Büyük/Küçük Harf Kuralları
description: Tanımlayıcılar, bileşik sözcükler ve genel terimler için büyük harfe çevirme kuralları uygulayın. .NET 'ta büyük/küçük harf duyarlılığı 'nın nasıl çalıştığını anlayın.
ms.date: 10/22/2008
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
ms.openlocfilehash: e416a8346952a41d9c89f526bfce990dfc277fc1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701269"
---
# <a name="capitalization-conventions"></a>Büyük/Küçük Harf Kuralları

Bu bölümdeki yönergeler, tutarlı bir şekilde uygulandığında, türler, Üyeler ve parametreler için tanımlayıcıların kolay okunmasını sağlamak üzere basit bir yöntem sağlar.

## <a name="capitalization-rules-for-identifiers"></a>Tanımlayıcılar için büyük harfe dönüştürme kuralları

 Bir Tanımlayıcıdaki sözcükleri ayırt etmek için, Tanımlayıcıdaki her sözcüğün ilk harfini büyük harfle yapın. Sözcükleri ayırt etmek için alt çizgi kullanmayın veya bu konuyla ilgili olarak tanımlayıcılardan herhangi bir yerde. Tanımlayıcının kullanılmasına bağlı olarak, tanımlayıcıları büyük harfle almanın iki uygun yolu vardır:

- Pascalbüyük harf

- Camelbüyük harf

 Parametre adları hariç tüm tanımlayıcılar için kullanılan Pascalas kuralı, aşağıdaki örneklerde gösterildiği gibi her sözcüğün ilk karakterini (uzunluğunun iki harfli kısaltmalarla birlikte) büyük harfe dönüştürür:

 `PropertyDescriptor`
 `HtmlTag`

 Aşağıdaki tanımlayıcıda gösterildiği gibi, iki harfli kısaltmalar için her iki harf de büyük harfli olan özel bir durum yapılır:

 `IOStream`

 Yalnızca parametre adları için kullanılan Camelas kuralı, aşağıdaki örneklerde gösterildiği gibi ilk sözcük hariç her sözcüğün ilk karakterini büyük harfe dönüştürür. Örnekte de gösterildiği gibi, Camel bir tanımlayıcıya başlayan iki harfli kısaltmalar her ikisi de küçük harftir.

 `propertyDescriptor`
 `ioStream`
 `htmlTag`

 ✔️, birden çok sözcükten oluşan tüm ortak üye, tür ve ad alanı adları için Pascalbüyük harfleri kullanır.

 ✔️ parametre adları için Camelum kullanın.

 Aşağıdaki tabloda, farklı türlerde tanımlayıcılar için büyük/küçük harf kuralları açıklanmaktadır.

|Tanımlayıcı|Büyük/Küçük Harf Kullanımı|Örnek|
|----------------|------------|-------------|
|Ad Alanı|Pascal|`namespace System.Security { ... }`|
|Tür|Pascal|`public class StreamReader { ... }`|
|Arabirim|Pascal|`public interface IEnumerable { ... }`|
|Yöntem|Pascal|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|
|Özellik|Pascal|`public class String {` <br />  `public int Length { get; }` <br /> `}`|
|Olay|Pascal|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|
|Alan|Pascal|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|
|Sabit listesi değeri|Pascal|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|
|Parametre|Ortası büyük harf|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|

## <a name="capitalizing-compound-words-and-common-terms"></a>Bileşik sözcüklerin ve ortak koşulların büyük bir olması

 Çoğu bileşik terim, büyük küçük harf amaçlarıyla tek sözcük olarak değerlendirilir.

 ❌ Bu nedenle, kapalı biçimli bileşik sözcükler olarak adlandırılan her sözcüğü büyük harfle kaldırmayın.

 Bunlar, uç nokta gibi tek bir kelime olarak yazılmış olan Birleşik sözcüklerdir. Büyük/küçük harf yönergeleri için kapalı biçimli bir bileşik sözcüğü tek bir sözcük olarak değerlendirin. Bileşik bir sözcüğün kapalı biçimde yazılıp yazılmadığını öğrenmek için geçerli bir sözlük kullanın.

|Pascal|Ortası büyük harf|Not|
|------------|-----------|---------|
|`BitFlag`|`bitFlag`|`Bitflag`|
|`Callback`|`callback`|`CallBack`|
|`Canceled`|`canceled`|`Cancelled`|
|`DoNot`|`doNot`|`Don't`|
|`Email`|`email`|`EMail`|
|`Endpoint`|`endpoint`|`EndPoint`|
|`FileName`|`fileName`|`Filename`|
|`Gridline`|`gridline`|`GridLine`|
|`Hashtable`|`hashtable`|`HashTable`|
|`Id`|`id`|`ID`|
|`Indexes`|`indexes`|`Indices`|
|`LogOff`|`logOff`|`LogOut`|
|`LogOn`|`logOn`|`LogIn`|
|`Metadata`|`metadata`|`MetaData, metaData`|
|`Multipanel`|`multipanel`|`MultiPanel`|
|`Multiview`|`multiview`|`MultiView`|
|`Namespace`|`namespace`|`NameSpace`|
|`Ok`|`ok`|`OK`|
|`Pi`|`pi`|`PI`|
|`Placeholder`|`placeholder`|`PlaceHolder`|
|`SignIn`|`signIn`|`SignOn`|
|`SignOut`|`signOut`|`SignOff`|
|`UserName`|`userName`|`Username`|
|`WhiteSpace`|`whiteSpace`|`Whitespace`|
|`Writable`|`writable`|`Writeable`|

## <a name="case-sensitivity"></a>Büyük/küçük harf duyarlılığı

 CLR üzerinde çalışabilen dillerin, büyük/küçük harf duyarlılığı desteklemek için gerekli değildir, ancak bazıları. Diliniz destekliyorsa bile, çerçeve'nize erişebilen diğer diller değildir. Bu nedenle dışarıdan erişilebilen tüm API 'Ler, aynı bağlamdaki iki ad arasında ayrım yapmak için tek başına bir durum kullanamaz.

 ❌ Tüm programlama dillerinin büyük/küçük harfe duyarlı olduğunu varsaymayın. Bunlar değildir. Adlar tek başına büyük/küçük harf bakımından farklı olamaz.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve tasarım yönergeleri](index.md)
- [Adlandırma yönergeleri](naming-guidelines.md)
