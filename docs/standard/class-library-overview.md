---
title: ".NET Framework Sınıf Kitaplığına Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- classes [.NET Framework], library overview
- class objects value type
- naming conventions [.NET Framework]
- types, .NET Framework
- user-defined types
- Visual Basic, data types
- data types [.NET Framework], C++
- Visual C#, data types
- libraries, .NET Framework class library
- data types [.NET Framework], JScript
- System namespace
- JScript, data types
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
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 607ef0020e15581c6ccca8f232eaea6be547f63b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="net-framework-class-library-overview"></a>.NET Framework Sınıf Kitaplığına Genel Bakış
[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Sınıfları ve arabirimleri hızlandırmak ve geliştirme sürecinin en iyi duruma getirme ve sistem işlevlere erişim sağlayan değer türleri içerir. Diller arasında birlikte çalışabilirlik kolaylaştırmak için çoğu .NET Framework türleri CLS ile uyumlu olan ve bu nedenle, derleyici ortak dil belirtimi (CLS) uyan herhangi bir programlama dili kullanılabilir.  
  
 .NET uygulamaları, bileşenleri ve denetimleri yerleşiktir foundation .NET Framework türleridir. [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Aşağıdaki işlevleri gerçekleştirir türleri içerir:  
  
-   Temel veri türlerini ve özel durumları temsil eder.  
  
-   Veri yapıları kapsüller.  
  
-   G/ç gerçekleştirin.  
  
-   Yüklenen türler hakkında bilgi erişim.  
  
-   .NET Framework güvenlik denetimlerini çağırır.  
  
-   Veri erişimi, zengin istemci-tarafı GUI ve sunucu tarafından denetlenen, istemci-tarafı GUI sağlar.  
  
 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Zengin bir soyut ve somut (soyut olmayan) sınıflar yanı sıra arabirimleri sağlar. Kendi sınıflarınızı aktarımlar, olduğu gibi veya pek çok durumda somut sınıflar kullanın. Arabirim işlevselliğini kullanmak için arabirimini uygulayan bir sınıf oluşturun veya arabirimini uygulayan .NET Framework sınıfları birinden bir sınıf türetin.  
  
## <a name="naming-conventions"></a>Adlandırma kuralları  
 .NET framework türleri bir hiyerarşi connotes nokta sözdizimini adlandırma şeması kullanın. Bunlar kullanılabilir aranır ve daha kolay başvurduğu için bu tekniği ad alanında ilgili türleri gruplandırır. Tam adı ilk bölümü — en sağdaki nokta kadar — ad alanı adı. Son adı tür adı parçasıdır. Örneğin, **System.Collections.ArrayList** temsil eden **ArrayList** ait olduğu tür **System.Collections** ad alanı. Türler **System.Collections** nesne koleksiyonları işlemek için kullanılabilir.  
  
 Bu adlandırma şeması genişletme kitaplığı geliştiriciler için kolaylaştırır [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] türleri hiyerarşik grupları oluşturmak ve bunları tutarlı ve bilgilendirici bir şekilde için. Ayrıca tam adına göre belirsizliğe tanımlanmasını türlerine izin verir (diğer bir deyişle, ad alanı ve tür adı), türü ad çakışmaları engeller. Aşağıdaki kural kendi ad alanları için adları oluşturulurken kullanılacak kitaplığı geliştiriciler bekleniyor:  
  
 *Şirket adı*. *TechnologyName*  
  
 Örneğin, ad alanı Microsoft.Word bu kılavuz için uygundur.  
  
 Grup için adlandırma modelleri kullanımını ad alanları türlerine oluşturmak ve belge sınıf kitaplıkları için çok kullanışlı bir yol ile ilgili. Ancak, bu adlandırma şeması görünürlük, üye erişimi, devralma, güvenlik veya bağlama üzerinde hiçbir etkisi yoktur. Bir ad alanı arasında birden çok derleme bölümlenebilir ve tek bir derleme birden çok ad alanını türlerinden içerebilir. Derleme sürümü oluşturma, dağıtım, güvenlik, yükleme ve ortak dil çalışma zamanı görünürlüğü resmi yapısı sağlar.  
  
 Ad alanları ve tür adları hakkında daha fazla bilgi için bkz: [ortak tür sistemi](../../docs/standard/base-types/common-type-system.md).  
  
## <a name="system-namespace"></a>Sistem Namespace  
 <xref:System> Ad alanıdır temel türleri için kök ad alanı [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Bu ad alanı, tüm uygulamaları tarafından kullanılan temel veri türlerini temsil eden sınıflar içerir: <xref:System.Object> (devralma hiyerarşisi kökündeki) <xref:System.Byte>, <xref:System.Char>, <xref:System.Array>, <xref:System.Int32>, <xref:System.String>ve benzeri. Bu tür pek çok programlama diliniz kullanan temel veri türleri karşılık gelir. .NET Framework türleri kullanarak kod yazarken dilinizi ait karşılık gelen anahtar sözcüğü bir .NET Framework temel veri türü beklenen zaman kullanabilirsiniz.  
  
 Aşağıdaki tabloda temel türleri [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] sağlayan, kısaca her türünü tanımlar ve Visual Basic, C#, C++ ve JScript karşılık gelen türünü gösterir.  
  
|Kategori|Sınıf adı|Açıklama|Visual Basic veri türü|C# veri türü|C++ veri türü|JScript veri türü|  
|--------------|----------------|-----------------|----------------------------|-------------------|---------------------|-----------------------|  
|Tamsayı|<xref:System.Byte>|Bir 8 bit işaretsiz tamsayıyı.|**Bayt**|**byte**|**İmzasız char**|**Bayt**|  
||<xref:System.SByte>|Bir 8 bit işaretli tamsayıyı.<br /><br /> Değil CLS ile uyumlu.|**SByte**|**sbyte**|**char**<br /><br /> veya<br /><br /> **İmzalı** **char**|**SByte**|  
||<xref:System.Int16>|Bir 16 bit işaretli tamsayıyı.|**Kısa**|**short**|**short**|**short**|  
||<xref:System.Int32>|32 bit imzalı bir tamsayı.|**Tamsayı**|**int**|**int**<br /><br /> veya<br /><br /> **long**|**int**|  
||<xref:System.Int64>|64-bit imzalı bir tamsayı.|**Uzun**|**long**|**__int64**|**long**|  
||<xref:System.UInt16>|Bir 16 bit işaretsiz tamsayı.<br /><br /> Değil CLS ile uyumlu.|**UShort**|**ushort**|**İmzasız short**|**UInt16**|  
||<xref:System.UInt32>|Bir 32 bit işaretsiz tamsayı.<br /><br /> Değil CLS ile uyumlu.|**Uınteger**|**uint**|**İmzasız int**<br /><br /> veya<br /><br /> **İmzasız long**|**UInt32**|  
||<xref:System.UInt64>|Bir 64-bit işaretsiz tamsayı.<br /><br /> Değil CLS ile uyumlu.|**ULong**|**ulong**|**İmzasız __int64**|**UInt64**|  
|Kayan nokta|<xref:System.Single>|Bir tek duyarlıklı (32 bit) kayan noktalı sayı.|**Tek**|**float**|**float**|**float**|  
||<xref:System.Double>|Bir çift duyarlıklı (64 bit) kayan noktalı sayı.|**Çift**|**double**|**double**|**double**|  
|Mantıksal|<xref:System.Boolean>|Bir Boole değeri (true veya false).|**Boole değeri**|**bool**|**bool**|**bool**|  
|Diğer|<xref:System.Char>|Unicode (16-bit) karakter.|**Char**|**char**|**wchar_t**|**char**|  
||<xref:System.Decimal>|Ondalık (128-bit) bir değer.|**Ondalık**|**decimal**|**Ondalık**|**Ondalık**|  
||<xref:System.IntPtr>|Temel alınan bir platform (32-bit değer 32-bit platformu üzerinde) ve bir 64-bit platformu üzerinde 64-bit değeri büyüklüğü bağlıdır imzalı bir tamsayı.|**IntPtr**<br /><br /> Yerleşik tür yok.|**IntPtr**<br /><br /> Yerleşik tür yok.|**IntPtr**<br /><br /> Yerleşik tür yok.|**IntPtr**|  
||<xref:System.UIntPtr>|İmzalanmamış tamsayı temel platform (32-bit değer 32-bit platformu üzerinde) ve bir 64-bit platformu üzerinde 64-bit değeri büyüklüğü bağlıdır.<br /><br /> Değil CLS ile uyumlu.|**UIntPtr**<br /><br /> Yerleşik tür yok.|**UIntPtr**<br /><br /> Yerleşik tür yok.|**UIntPtr**<br /><br /> Yerleşik tür yok.|**UIntPtr**|  
ASS nesneleri|<xref:System.Object>|Nesne hiyerarşisinin kökü.|**Nesne**|**object**|**Nesne\***|**Nesne**|  
||<xref:System.String>|Unicode karakterden oluşan bir değişmez, sabit uzunluklu dize.|**Dize**|**string**|**Dize\***|**Dize**|  
  
 Temel veri türlerini yanı sıra <xref:System> ad alanı, uygulama etki alanları ve atık toplayıcı gibi temel çalışma zamanı kavramlar uğraşmanız sınıfları için özel durumları işleme sınıflar arasında değişen 100'den sınıfları içerir. <xref:System> Ad alanı da birçok ikinci düzey ad alanları içerir.  
  
 Ad alanları hakkında daha fazla bilgi için Gözat [.NET Framework sınıf kitaplığı](http://go.microsoft.com/fwlink/?LinkID=227195). Başvuru belgeleri her ad alanı kısa bir genel bakış ve aynı zamanda her tür ve üyeleri resmi bir açıklama sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ortak Tür Sistemi](../../docs/standard/base-types/common-type-system.md)  
 [.NET framework sınıf kitaplığı](http://go.microsoft.com/fwlink/?LinkID=227195)  
 [Genel bakış](../../docs/framework/get-started/overview.md)
