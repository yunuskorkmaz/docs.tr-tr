---
title: "Büyük/küçük harf kuralları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b36f230c9a5f8653f3e252d26fe6464bb9cac4bb
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="capitalization-conventions"></a>Büyük/küçük harf kuralları
Bu bölüm yerleşim kullanmak için basit bir yöntem çıkışı yönergeleri, sürekli türleri, üyeleri ve parametreleri okumak kolay yapma tanımlayıcıları uygulandığında durumda.  
  
## <a name="capitalization-rules-for-identifiers"></a>Tanımlayıcılar için büyük/küçük harf kuralları  
 Tanımlayıcı sözcükleri ayırt etmek için tanımlayıcı her sözcüğün ilk harfini büyük harf. Alt çizgi sözcükleri ayırt etmek için kullanmayın veya tanımlayıcıları başka bir yerindeki Bu konular için. Tanımlayıcı kullanılmasına bağlı olarak tanımlayıcıları sağladığınızdan uygun iki yolu vardır:  
  
-   PascalCasing  
  
-   camelCasing  
  
 Parametre adları dışındaki tüm tanımlayıcılar için kullanılan PascalCasing kuralı (iki harf uzunluğu üzerinden kısaltmalar dahil) her sözcüğün ilk karakteri aşağıdaki örneklerde gösterildiği gibi büyük harfe çevirir:  
  
 `PropertyDescriptor`  
 `HtmlTag`  
  
 Özel bir durum içinde her iki harf olduğundan, iki harfli kısaltmalar için aşağıdaki tanımlayıcıda gösterildiği gibi yapılır:  
  
 `IOStream`  
  
 Parametre adları için yalnızca kullanılan camelCasing kuralı ilk word dışında her sözcüğün ilk karakteri aşağıdaki örneklerde gösterildiği gibi büyük harfe dönüştürür. Örnekte de görüldüğü gibi bir başlamalıdır tanımlayıcı başlamak iki harfli kısaltmalar küçük hem de ' dir.  
  
 `propertyDescriptor`  
 `ioStream`  
 `htmlTag`  
  
 **✓ YAPMAK** PascalCasing birden çok sözcüklük oluşan tüm ortak üye, türü ve ad alanı adları için kullanın.  
  
 **✓ YAPMAK** camelCasing parametre adları için kullanın.  
  
 Aşağıdaki tabloda, farklı türlerdeki tanımlayıcıları için büyük/küçük harf kurallar açıklanmaktadır.  
  
|Tanımlayıcı|Büyük/küçük harf kullanımı|Örnek|  
|----------------|------------|-------------|  
|Ad Alanı|Pascal|`namespace System.Security { ... }`|  
|Tür|Pascal|`public class StreamReader { ... }`|  
|Arabirim|Pascal|`public interface IEnumerable { ... }`|  
|Yöntem|Pascal|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|  
|Özellik|Pascal|`public class String {` <br />  `public int Length { get; }` <br /> `}`|  
|Olay|Pascal|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|  
|Alan|Pascal|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|  
|Enum değeri|Pascal|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|  
|Parametre|Ortası büyük|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|  
  
## <a name="capitalizing-compound-words-and-common-terms"></a>Bileşik sözcüklerin ve Ortak terimleri büyük harfe dönüştürme  
 Çoğu bileşik koşulları büyük/küçük harf amaçları için tek sözcük olarak kabul edilir.  
  
 **X yok** sözde kapalı form bileşik sözcüklerin her sözcüğün büyük harfe çevirme.  
  
 Bu uç nokta gibi tek bir sözcük olarak yazılmış bileşik sözcüklerdir. Büyük/küçük harf yönergeleri amacıyla kapalı form bileşik word tek bir sözcük kabul eder. Geçerli bir sözlük, bileşik bir sözcük kapalı formunda yazılırsa belirlemek için kullanın.  
  
|Pascal|Ortası büyük|değil|  
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
 Bazı yapmak rağmen üzerinde CLR çalıştırabilirsiniz dilleri büyük küçük harf duyarlılığı, desteklemek için gereken değil. Dilinizi desteklediği olsa bile, framework erişebilir diğer diller yoktur. Harici olarak erişilebilir olan tüm API'ları bu nedenle, tek başına aynı bağlamda iki ad arasında ayrım yapmak için durumu güvenir olamaz.  
  
 **X yok** tüm programlama dilleriyle büyük küçük harfe duyarlı olduğunu varsayar. Bunlar değildir. Adları örneği tarafından tek başına farklı olamaz.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
 [Adlandırma Kuralları](../../../docs/standard/design-guidelines/naming-guidelines.md)
