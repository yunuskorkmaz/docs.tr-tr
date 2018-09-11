---
title: Büyük/küçük harf kuralları
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 070fc69728c2cb38e465dab9f6f591a77a857531
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44274272"
---
# <a name="capitalization-conventions"></a>Büyük/küçük harf kuralları
Yönergeleri bu bölümün yerleşim kullanmak için basit bir yöntemini, tutarlı bir şekilde, türleri, üyeler ve parametreler okuması yapma tanımlayıcıları uygulandığında durumda.  
  
## <a name="capitalization-rules-for-identifiers"></a>Tanımlayıcıların büyük/küçük harf kuralları  
 Bir tanımlayıcı sözcükleri ayırt etmek için tanımlayıcının her sözcüğün ilk harfini büyük harfe Dönüştür. Sözcükleri ayırmak için alt çizgi kullanmayın veya tanımlayıcıları herhangi bir yerinden, sorgunuzun. Büyük harf tanımlayıcıları, tanımlayıcı kullanılmasına bağlı olarak uygun iki yolu vardır:  
  
-   PascalCasing  
  
-   camelCasing  
  
 Parametre adları hariç tüm tanımlayıcıları için kullanılan PascalCasing kural, ilk karakter (iki harf uzunluğu üzerinde kısaltmalar dahil), her bir sözcüğün aşağıdaki örneklerde gösterildiği gibi büyük harfe dönüştürür:  
  
 `PropertyDescriptor`  
 `HtmlTag`  
  
 Özel bir durum, her iki harf olduğundan, iki harfli kısaltmalar için aşağıdaki tanımlayıcıda gösterildiği şekilde yapılır:  
  
 `IOStream`  
  
 Parametre adları için yalnızca kullanılan camelCasing kural, aşağıdaki örneklerde gösterildiği gibi her sözcüğün ilk sözcük dışındaki ilk karakteri büyük harfe dönüştürür. Örnekte de gösterildiği gibi bir başlamalıdır tanımlayıcı başlayan iki harfli kısaltmalar hem küçük olan.  
  
 `propertyDescriptor`  
 `ioStream`  
 `htmlTag`  
  
 **✓ DO** PascalCasing birden çok sözcüklük oluşan tüm ortak üye, türü ve ad alanı adları için kullanın.  
  
 **✓ DO** camelCasing parametre adları için kullanın.  
  
 Aşağıdaki tabloda, farklı tür tanımlayıcıları büyük/küçük harf kurallarını açıklar.  
  
|tanımlayıcı|Büyük/küçük harf kullanımı|Örnek|  
|----------------|------------|-------------|  
|Ad Alanı|Pascal|`namespace System.Security { ... }`|  
|Tür|Pascal|`public class StreamReader { ... }`|  
|Arabirim|Pascal|`public interface IEnumerable { ... }`|  
|Yöntem|Pascal|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|  
|Özellik|Pascal|`public class String {` <br />  `public int Length { get; }` <br /> `}`|  
|Olay|Pascal|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|  
|Alan|Pascal|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|  
|Sabit listesi değeri|Pascal|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|  
|Parametre|Ortası|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|  
  
## <a name="capitalizing-compound-words-and-common-terms"></a>Bileşik sözcüklerin büyük harfe dönüştürme ve genel koşulları  
 Çoğu bileşik koşulları büyük/küçük harf amaçları için tek sözcük olarak kabul edilir.  
  
 **X DO NOT** sözde kapalı form bileşik sözcüklerin her sözcüğün büyük harfe çevirme.  
  
 Bu uç nokta gibi tek bir sözcük olarak yazılan bileşik sözcüklerdir. Büyük/küçük harf kuralları amacıyla kapalı biçimli bir bileşik sözcük tek bir sözcük kabul eder. Bir bileşik sözcük kapalı formunda yazılırsa belirlemek için geçerli bir sözlük kullanın.  
  
|Pascal|Ortası|değil|  
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
  
## <a name="case-sensitivity"></a>Büyük/küçük harfe duyarlılık  
 Bazı yapın, ancak CLR üzerinde çalışabilen dilleri büyük küçük harf duyarlılığı, desteklemek için gerekli değildir. Dilinizi desteklediği bile Çerçevenizi erişebilecek diğer diller yoktur. Harici olarak erişilebilen herhangi bir API, bu nedenle, tek başına, aynı bağlamda iki ad arasında ayrım yapmak için servis talebi üzerinde güvenemezsiniz.  
  
 **X DO NOT** tüm programlama dilleriyle büyük küçük harfe duyarlı olduğunu varsayar. Değiller. Adlar tek başına harfe göre farklılık göstermeyebilir.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
- [Adlandırma Kuralları](../../../docs/standard/design-guidelines/naming-guidelines.md)
