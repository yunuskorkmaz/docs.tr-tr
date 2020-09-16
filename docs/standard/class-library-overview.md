---
title: .NET sınıf kitaplığına genel bakış
description: .NET sınıf kitaplığı hakkında bilgi edinin. .NET uygulamaları, sistem işlevlerine erişim sağlamak için sınıflar, arabirimler, temsilciler ve değer türlerini içerir.
ms.date: 02/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET Framework], library overview
- classes [.NET Core], library overview
- .NET, library overview
- class objects value type
- naming conventions [.NET Framework]
- types, .NET Framework
- user-defined types
- Visual Basic, data types
- data types [.NET Framework], C++
- Visual C#, data types
- libraries, .NET Framework class library
- data types [.NET Framework], F#
- System namespace
- F#, data types
- .NET Framework, class library
- type system [.NET Framework]
- data types [.NET Framework]
- value types
- data types [.NET Framework], Visual Basic
- Common Language Specification
- namespaces [.NET Framework]
- floating point value type
- class library [.NET Framework]
- CLS
- logical value type
- .NET Framework class library, about
- built-in types
- namespaces [.NET Framework], about namespaces
- Visual C++, data types
- members [.NET Framework], type
- data types [.NET Framework], C#
- integer value type
- base types, class library
ms.assetid: 7e4c5921-955d-4b06-8709-101873acf157
ms.openlocfilehash: cf2137c2ebd2f4901401ed25746febaa440a08f5
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554768"
---
# <a name="net-class-library-overview"></a>.NET sınıf kitaplığına genel bakış

.NET uygulamaları, geliştirme sürecini hızlandırmak ve iyileştirmek ve sistem işlevlerine erişim sağlamak için sınıflar, arabirimler, temsilciler ve değer türlerini içerir. Diller arasında birlikte çalışabilirliği kolaylaştırmak için, çoğu .NET türü CLS uyumludur ve bu nedenle, derleyicisinin ortak dil belirtimine (CLS) uygun olan herhangi bir programlama dilinden kullanılabilir.  
  
 .NET türleri, .NET uygulamaları, bileşenleri ve denetimlerinin oluşturulduğu temel uygulamalardır. .NET uygulamaları aşağıdaki işlevleri gerçekleştiren türleri içerir:  
  
- Temel veri türlerini ve özel durumları temsil eder.  
  
- Veri yapılarını yalıt.  
  
- G/ç gerçekleştirin.  
  
- Yüklenen türlerle ilgili bilgilere erişin.  
  
- .NET Framework güvenlik denetimlerini çağır.  
  
- Veri erişimi, zengin istemci tarafı GUI ve sunucu denetimli, istemci tarafı GUI sağlar.  
  
 .NET, soyut ve somut (soyut olmayan) sınıfların yanı sıra zengin bir arabirim kümesi sağlar. Somut sınıfları olduğu gibi kullanabilir veya çoğu durumda kendi sınıflarınızı bunlardan türetebilirsiniz. Bir arabirimin işlevselliğini kullanmak için, arabirimini uygulayan bir sınıf oluşturabilir veya arabirimini uygulayan .NET sınıflarından birinden bir sınıf türetebilirsiniz.  
  
## <a name="naming-conventions"></a>Adlandırma kuralları

 .NET türleri bir hiyerarşiyi karşılayan bir nokta sözdizimi adlandırma şeması kullanır. Bu teknik, arama yapmak ve daha kolay başvurulabilmeleri için ilgili türleri ad alanları halinde gruplandırır. Tam adın ilk bölümü — en sağdaki noktaya kadar — ad alanı adıdır. Adın son bölümü tür adıdır. Örneğin, `System.Collections.Generic.List<T>` `List<T>` ad alanına ait olan türü temsil eder `System.Collections.Generic` . İçindeki türler <xref:System.Collections.Generic> genel koleksiyonlarla çalışmak için kullanılabilir.  
  
 Bu adlandırma şeması, .NET Framework genişleten kitaplık geliştiricilerinin hiyerarşik tür grupları oluşturmasını ve bunları tutarlı, bilgilendirici bir şekilde adlandırmasını kolaylaştırır. Ayrıca, türlerin tam adı (yani ad alanı ve tür adlarıyla) tarafından kesin bir şekilde tanımlanmasına izin verir ve bu da tür adı çakışmalarını önler. Kitaplık geliştiricilerinin ad alanları için ad oluştururken aşağıdaki kuralı kullanması beklenir:  
  
 *CompanyName*. *TechnologyName*  
  
 Örneğin, ad alanı `Microsoft.Word` bu kılavuza uyar.  
  
 İlgili türleri ad alanlarına gruplamak için adlandırma desenlerinin kullanımı, sınıf kitaplıklarını derlemek ve belgelemek için çok faydalı bir yoldur. Ancak, bu adlandırma şemasının görünürlük, üye erişimi, devralma, güvenlik veya bağlama üzerinde hiçbir etkisi yoktur. Bir ad alanı birden çok derlemede bölümlenebilir ve tek bir derleme birden çok ad alanından türleri içerebilir. Derleme, ortak dil çalışma zamanında sürüm oluşturma, dağıtım, güvenlik, yükleme ve görünürlük için biçimsel yapı sağlar.  
  
 Ad alanları ve tür adları hakkında daha fazla bilgi için bkz. [ortak tür sistemi](base-types/common-type-system.md).  
  
## <a name="system-namespace"></a>Sistem ad alanı

 <xref:System>Ad alanı, .net 'teki temel türler için kök ad alanıdır. Bu ad alanı, tüm uygulamalar tarafından kullanılan temel veri türlerini temsil eden sınıfları içerir: <xref:System.Object> (devralma hiyerarşisinin kökü),,,,, vb <xref:System.Byte> <xref:System.Char> <xref:System.Array> <xref:System.Int32> <xref:System.String> . Bu türlerin çoğu, programlama dilinizin kullandığı temel veri türlerine karşılık gelir. .NET Framework türlerini kullanarak kod yazdığınızda, bir .NET Framework temel veri türü beklendiğinde dilinizin karşılık gelen anahtar sözcüğünü kullanabilirsiniz.  
  
 Aşağıdaki tabloda, .NET 'in sağladığı temel türler listelenmekte, her tür kısaca açıklanmakta ve Visual Basic, C#, C++ ve F # içinde karşılık gelen tür gösterilmektedir.  
  
|Kategori|Sınıf adı|Description|Visual Basic veri türü|C# veri türü|C++/CLı veri türü|F # veri türü|  
|--------------|----------------|-----------------|----------------------------|-------------------|---------------------|-----------------------|  
|Tamsayı|<xref:System.Byte>|8 bit işaretsiz tamsayı.|**Bayt**|**bayt**|**unsigned char**|**bayt**|  
||<xref:System.SByte>|8 bit işaretli tamsayı.<br /><br /> CLS uyumlu değildir.|**SByte**|**SByte**|**char**<br /> -veya-<br /> **işaretli** **karakter**|**SByte**|  
||<xref:System.Int16>|16 bit işaretli tamsayı.|**Kısadır**|**short**|**short**|**Int16**|  
||<xref:System.Int32>|32 bitlik işaretli tamsayı.|**Gir**|**int**|**int**<br /><br /> -veya-<br /><br /> **long**|**int**|  
||<xref:System.Int64>|64 bitlik işaretli tamsayı.|**Kalacağını**|**long**|**__int64**|**tutulamaz**|  
||<xref:System.UInt16>|16 bitlik işaretsiz tamsayı.<br /><br /> CLS uyumlu değildir.|**UShort**|**ushort**|**imzasız short**|**Int16**|  
||<xref:System.UInt32>|32 bitlik işaretsiz tamsayı.<br /><br /> CLS uyumlu değildir.|**UInteger**|**uint**|**unsigned int**<br /> -veya-<br /> **imzasız long**|**Int32**|  
||<xref:System.UInt64>|64 bitlik işaretsiz tamsayı.<br /><br /> CLS uyumlu değildir.|**'Tur**|**ulong**|**imzasız __int64**|**Int64**|  
|Kayan nokta|<xref:System.Single>|Tek duyarlıklı (32-bit) kayan noktalı sayı.|**Tek**|**float**|**float**|**float32**<br> veya<br>**sunuculu**|  
||<xref:System.Double>|Çift duyarlıklı (64-bit) kayan noktalı sayı.|**Çift**|**double**|**double**|**float**<br> veya <br> **double**|  
|Mantıksal|<xref:System.Boolean>|Boole değeri (true veya false).|**Boole**|**bool**|**bool**|**bool**|  
|Diğer|<xref:System.Char>|Unicode (16 bit) karakteri.|**Char**|**char**|**wchar_t**|**char**|  
||<xref:System.Decimal>|Ondalık (128-bit) bir değer.|**Kategori**|**decimal**|**Kategori**|**decimal**|  
||<xref:System.IntPtr>|Boyutu temel platforma bağlı olan işaretli bir tamsayı (32 bit platformda 32 bitlik bir değer ve bir 64-bit platformunda 64 bit değeri).|**Serisi**<br /><br /> Yerleşik tür yok.|**Serisi**<br /><br /> Yerleşik tür yok.|**Serisi**<br /><br /> Yerleşik tür yok.|**unativeint**|  
||<xref:System.UIntPtr>|Boyutu temeldeki platforma bağlı işaretsiz bir tamsayı (32 bitlik bir platformda 32 bitlik bir değer ve bir 64-bit platformunda 64 bit değeri).<br /><br /> CLS uyumlu değildir.|**UIntPtr**<br /><br /> Yerleşik tür yok.|**UIntPtr**<br /><br /> Yerleşik tür yok.|**UIntPtr**<br /><br /> Yerleşik tür yok.|**unativeint**|  
||<xref:System.Object>|Nesne hiyerarşisinin kökü.|**Nesne**|**object**|**Nesne ^**|**obj**|  
||<xref:System.String>|Unicode karakterlerinden oluşan sabit ve sabit uzunlukta bir dize.|**Dize**|**string**|**Dize ^**|**string**|  
  
 Temel veri türlerine ek olarak, <xref:System> ad alanı, uygulama etki alanları ve çöp toplayıcı gibi çekirdek çalışma zamanı kavramlarıyla ilgilenen sınıflarda özel durumları işleyen sınıflardan farklı olarak 100 ' den fazla sınıf içerir. <xref:System>Ad alanı da birçok ikinci düzey ad alanı içerir.  
  
 Ad alanları hakkında daha fazla bilgi için .net [API tarayıcısı](../../api/index.md) ' nı kullanarak .NET sınıf kitaplığı 'na gidin. API başvuru belgeleri, her bir ad alanı, türleri ve üyelerinin her biri için belgeler sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ortak tür sistemi](base-types/common-type-system.md)
- [.NET API tarayıcısı](../../api/index.md)
- [Genel bakış](../framework/get-started/overview.md)
