---
title: .NET sınıf kitaplığı genel bakış
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
ms.openlocfilehash: 596c0fd8fec8f59d977f1db445f9000df23ad5ce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400486"
---
# <a name="net-class-library-overview"></a>.NET sınıf kitaplığı genel bakış

.NET uygulamaları, geliştirme işlemini hızlandıran ve optimize eden ve sistem işlevselliği sağlayan sınıflar, arabirimler, temsilciler ve değer türlerini içerir. Diller arasında birlikte çalışabilirliği kolaylaştırmak için, çoğu .NET türü CLS uyumludur ve bu nedenle derleyiciortak dil belirtimine (CLS) uygun olan herhangi bir programlama dilinden kullanılabilir.  
  
 .NET türleri,.NET uygulamalarının, bileşenlerinin ve denetimlerinin temelidir. .NET uygulamaları aşağıdaki işlevleri gerçekleştiren türleri içerir:  
  
- Temel veri türlerini ve özel durumlarını temsil eder.  
  
- Veri yapılarını kapsülle.  
  
- I/O gerçekleştirin.  
  
- Yüklenen türler hakkındaki bilgilere erişin.  
  
- .NET Framework güvenlik denetimlerini çağırın.  
  
- Veri erişimi, zengin istemci tarafı GUI ve sunucu kontrollü, istemci tarafı GUI sağlayın.  
  
 .NET, zengin bir arabirim kümesinin yanı sıra soyut ve somut (soyut olmayan) sınıflar da sağlar. Somut sınıfları olduğu gibi kullanabilir veya birçok durumda kendi sınıflarınızı onlardan türetebilirsiniz. Arabirimin işlevselliğini kullanmak için, arabirimi uygulayan bir sınıf oluşturabilir veya arabirimi uygulayan .NET sınıflarından birinden bir sınıf türetebilirsiniz.  
  
## <a name="naming-conventions"></a>Adlandırma kuralları

 .NET türleri, bir hiyerarşiyi ifade eden nokta sözdizimi adlandırma düzeni kullanır. Bu teknik, ilgili türleri ad alanlarına gruplandırarak daha kolay aranıp başvurulabilmeleri için gruplandırılır. Tam adın ilk bölümü - en sağdaki nokta - ad alanı adıdır. Adın son bölümü tür adıdır. Örneğin, `System.Collections.Generic.List<T>` `System.Collections.Generic` ad `List<T>` alanına ait türü temsil eder. Bu tür <xref:System.Collections.Generic> genel koleksiyonlarla çalışmak için kullanılabilir.  
  
 Bu adlandırma şeması, kütüphane geliştiricilerinin .NET Framework'ü genişleterek hiyerarşik tür grupları oluşturmasını ve bunları tutarlı ve bilgilendirici bir şekilde adlandırmasını kolaylaştırır. Ayrıca, türlerin tam adlarıyla (diğer bir şekilde ad alanı ve tür adı ile) kesin olarak tanımlanmasına izin verir ve bu da tür adı çakışmalarını önler. Kitaplık geliştiricilerin ad alanları için ad oluştururken aşağıdaki kuralı kullanmaları beklenir:  
  
 *Şirket Adı*. *TechnologyName*  
  
 Örneğin, ad alanı `Microsoft.Word` bu kılavuza uygundur.  
  
 İlişkili türleri ad alanlarına gruplandırmak için adlandırma desenleri kullanımı, sınıf kitaplıkları oluşturmak ve belgelemek için çok yararlı bir yoldur. Ancak, bu adlandırma düzeninin görünürlük, üye erişimi, devralma, güvenlik veya bağlama üzerinde hiçbir etkisi yoktur. Ad alanı birden çok derleme arasında bölümlenebilir ve tek bir derleme birden çok ad alanından türler içerebilir. Derleme, ortak dil çalışma zamanında sürüm, dağıtım, güvenlik, yükleme ve görünürlük için resmi bir yapı sağlar.  
  
 Ad alanları ve tür adları hakkında daha fazla bilgi için [Ortak Tür Sistemi'ne](../../docs/standard/base-types/common-type-system.md)bakın.  
  
## <a name="system-namespace"></a>Sistem ad alanı

 Ad <xref:System> alanı,.NET'teki temel türlerin kök ad alanıdır. Bu ad alanı, tüm uygulamalar tarafından kullanılan temel <xref:System.Object> veri türlerini temsil eden <xref:System.Byte>sınıfları içerir: (kalıtım hiyerarşisinin kökü), , , <xref:System.Char> <xref:System.Array> <xref:System.Int32>, <xref:System.String>, , vb. Bu türlerin çoğu, programlama dilinizin kullandığı ilkel veri türlerine karşılık gelir. .NET Framework türlerini kullanarak kod yazarken, .NET Framework base veri türü beklendiğinde dilinizin karşılık gelen anahtar sözcüklerini kullanabilirsiniz.  
  
 Aşağıdaki tabloda .NET'in sağladığı temel türleri listeler, her türü kısaca açıklar ve Visual Basic, C#, C++ve F#'da karşılık gelen türü gösterir.  
  
|Kategori|Sınıf adı|Açıklama|Visual Basic veri türü|C# veri türü|C++/CLI veri türü|F# veri türü|  
|--------------|----------------|-----------------|----------------------------|-------------------|---------------------|-----------------------|  
|Tamsayı|<xref:System.Byte>|8 bit imzasız bir sonda.|**Bayt**|**Bayt**|**unsigned char**|**Bayt**|  
||<xref:System.SByte>|8 bitlik imzalı bir sonda.<br /><br /> CLS uyumlu değil.|**Sbyte**|**Sbyte**|**char**<br /> -veya-<br /> **imzalı** **char**|**Sbyte**|  
||<xref:System.Int16>|16 bit imzalı tamsayı.|**Kısa**|**short**|**short**|**int16**|  
||<xref:System.Int32>|32 bit imzalı tamsayı.|**Tamsayı**|**int**|**int**<br /><br /> -veya-<br /><br /> **long**|**int**|  
||<xref:System.Int64>|64 bit imzalı tamsayı.|**Uzun**|**long**|**__int64**|**int64**|  
||<xref:System.UInt16>|16 bit imzasız tamsayı.<br /><br /> CLS uyumlu değil.|**Ushort**|**ushort**|**imzasız short**|**uint16**|  
||<xref:System.UInt32>|32 bit imzasız tamsayı.<br /><br /> CLS uyumlu değil.|**Uınteger**|**Uint**|**unsigned int**<br /> -veya-<br /> **imzasız long**|**uint32**|  
||<xref:System.UInt64>|64 bit imzasız tamsayı.<br /><br /> CLS uyumlu değil.|**Ulong**|**ulong**|**imzasız __int64**|**uint64**|  
|Kayan nokta|<xref:System.Single>|Tek duyarlıklı (32 bit) kayan nokta numarası.|**Tek**|**float**|**float**|**Float32**<br> or<br>**Tek**|  
||<xref:System.Double>|Çift duyarlıklı (64 bit) kayan nokta numarası.|**Çift**|**double**|**double**|**float**<br> or <br> **double**|  
|Mantıksal|<xref:System.Boolean>|Boolean değeri (doğru veya yanlış).|**Boole**|**bool**|**bool**|**bool**|  
|Diğer|<xref:System.Char>|Unicode (16-bit) karakter.|**Char**|**char**|**wchar_t**|**char**|  
||<xref:System.Decimal>|Ondalık (128-bit) bir değer.|**On -da -lık**|**decimal**|**On -da -lık**|**decimal**|  
||<xref:System.IntPtr>|Boyutu temel platforma (32 bit platformda 32 bit lik bir değer ve 64 bit platformda 64 bit lik bir değer) bağlı olan imzalı bir tamsayı.|**ıntptr**<br /><br /> Yerleşik bir tür yok.|**ıntptr**<br /><br /> Yerleşik bir tür yok.|**ıntptr**<br /><br /> Yerleşik bir tür yok.|**Unativeint**|  
||<xref:System.UIntPtr>|Boyutu temel platforma (32 bit platformda 32 bit lik bir değer ve 64 bit platformda 64 bit lik bir değer) bağlı olan imzasız bir tamsayı.<br /><br /> CLS uyumlu değil.|**Uıntptr**<br /><br /> Yerleşik bir tür yok.|**Uıntptr**<br /><br /> Yerleşik bir tür yok.|**Uıntptr**<br /><br /> Yerleşik bir tür yok.|**Unativeint**|  
||<xref:System.Object>|Nesne hiyerarşisinin kökü.|**Nesne**|**Nesne**|**Nesne^**|**obj**|  
||<xref:System.String>|Değişmez, sabit uzunlukta Unicode karakter dizesi.|**Dize**|**Dize**|**Dize^**|**Dize**|  
  
 Ad alanı, temel veri <xref:System> türlerine ek olarak, özel durumları işleyen sınıflardan uygulama etki alanları ve çöp toplayıcı gibi temel çalışma zamanı kavramlarıyla ilgili sınıflara kadar 100'den fazla sınıf içerir. Ad <xref:System> alanı da birçok ikinci düzey ad alanları içerir.  
  
 Ad alanları hakkında daha fazla bilgi için .NET Sınıf Kitaplığı'na göz atmak için [.NET API Tarayıcısını](https://docs.microsoft.com/dotnet/api) kullanın. API başvuru belgeleri, her ad alanı, türleri ve üyelerinin her biri hakkında belgeler sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ortak Tür Sistemi](../../docs/standard/base-types/common-type-system.md)
- [.NET API Tarayıcısı](../../api/index.md)
- [Genel bakış](../../docs/framework/get-started/overview.md)
