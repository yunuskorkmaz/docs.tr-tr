---
title: .NET sınıf kitaplığına genel bakış
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: acc51287a8c670da63d0ec421aa232864ea91c2b
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46580544"
---
# <a name="net-class-library-overview"></a>.NET sınıf kitaplığına genel bakış

.NET uygulamaları, sınıflar, arabirimler, temsilciler ve geliştirme işlemini hızlandırmak ve sistem işlevlerine erişmek için bir değer türleri içerir. Diller arasında birlikte çalışabilirlik kolaylaştırmak için çoğu .NET türleri CLS uyumludur ve bu nedenle, derleyici ortak dil belirtimi (CLS) uyumlu herhangi bir programlama dilinde kullanılabilir.  
  
 .NET, .NET uygulamalarının, bileşenlerinin ve denetimlerinin temel türleridir. .NET uygulamaları, şu işlevleri gerçekleştirmesini türleri şunlardır:  
  
-   Temel veri türlerini ve özel durumları temsil eder.  
  
-   Veri yapıları kapsüller.  
  
-   G/ç gerçekleştirin.  
  
-   Yüklenen türleri hakkında bilgi erişim.  
  
-   .NET Framework güvenlik denetimlerinden çağırın.  
  
-   Veri erişimi, zengin istemci tarafı GUI ve sunucu tarafından denetlenen, istemci tarafı GUI sağlar.  
  
 .NET zengin bir soyut ve somut (soyut olmayan) sınıflarının yanı sıra arabirimleri sağlar. Kendi sınıflarınızı aktarımlar, olduğu gibi veya pek çok durumda somut sınıflar'ı kullanın. Bir arabirimin işlevselliğini kullanmak için bir arabirimi uygulayan bir sınıf oluşturabilir veya arabirimi uygulayan .NET sınıflarının birinden bir sınıf türetin.  
  
## <a name="naming-conventions"></a>Adlandırma kuralları

 .NET türlerini bir hiyerarşi connotes nokta sözdizimini adlandırma şeması kullanır. Aranan edilebilmeleri ve daha kolay başvuru için bu tekniği ilgili türleri ad alanında gruplandırır. Tam adının ilk bölümü — en sağdaki nokta kadar — ad uzayı adıdır. Ad son kısmını tür adıdır. Örneğin, `System.Collections.Generic.List<T>` temsil `List<T>` ait olduğu tür `System.Collections.Generic` ad alanı. Türlerinde <xref:System.Collections.Generic> genel koleksiyonlar ile çalışma için kullanılabilir.  
  
 Bu adlandırma şeması genişletme kitaplığı geliştiriciler için kolaylaştıran [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] türlerinin hiyerarşik gruplar oluşturup bunları bilgilendirici tutarlı bir şekilde adlandırın. Ayrıca tam adına göre kesin bir şekilde tanımlanması türleri sağlar (diğer bir deyişle, kendi ad alanı ve türü adına göre), tür adı çakışmaları önler. Aşağıdaki kural adlarını kendi ad alanları için oluştururken kullanılacak kitaplığı geliştiriciler bekleniyor:  
  
 *CompanyName*. *TechnologyName*  
  
 Örneğin, ad alanı `Microsoft.Word` bu kılavuz için uygun.  
  
 Ad alanları türlerine, yapı ve sınıf kitaplıkları belge çok kullanışlı bir yöntemdir grubuna adlandırma modelleri kullanımını ilgili. Ancak, bu adlandırma şeması görünürlük, üye erişimi, devralma, güvenlik veya bağlama üzerinde etkisi yoktur. Bir ad alanı üzerinde birden çok derleme bölümlenebilir ve tek bir derleme türü birden çok ad alanından içerebilir. Derleme, sürüm oluşturma, dağıtım, güvenlik, yükleme ve ortak dil çalışma zamanı görünürlük için biçimsel yapısı sağlar.  
  
 Ad alanları ve tür adları hakkında daha fazla bilgi için bkz. [ortak tür sistemi](../../docs/standard/base-types/common-type-system.md).  
  
## <a name="system-namespace"></a>Sistem ad alanı

 <xref:System> Kök ad alanı .NET içinde temel türler için ad alanıdır. Bu ad alanı, tüm uygulamalar tarafından kullanılan temel veri türlerini temsil eden sınıfları içerir: <xref:System.Object> (devralma hiyerarşisinin kökü) <xref:System.Byte>, <xref:System.Char>, <xref:System.Array>, <xref:System.Int32>, <xref:System.String>ve benzeri. Bu tür pek çok programlama dilini kullanan ilkel veri türleri karşılık gelir. .NET Framework türleri kullanarak kod yazdığınızda, dilinizle ilgili anahtar sözcüğü bir .NET Framework temel veri türü beklenen zaman kullanabilirsiniz.  
  
 Aşağıdaki tablo .NET sağlar, kısaca her türünü tanımlar ve Visual Basic, C#, C++ ve F # içinde karşılık gelen tür gösterir, temel türleri listeler.  
  
|Kategori|Sınıf adı|Açıklama|Visual Basic veri türü|C# veri türü|C + +/ CLI veri türü|F # veri türü|  
|--------------|----------------|-----------------|----------------------------|-------------------|---------------------|-----------------------|  
|Tamsayı|<xref:System.Byte>|8 bitlik işaretsiz tamsayı.|**Bayt**|**byte**|**İmzasız char**|**byte**|  
||<xref:System.SByte>|Bir 8 bit işaretli tamsayı.<br /><br /> CLS uyumlu değil.|**SByte**|**sbyte**|**char**<br /> veya<br /> **İmzalı** **char**|**sbyte**|  
||<xref:System.Int16>|Bir 16 bitlik işaretli tamsayı.|**kısa**|**short**|**short**|**Int16**|  
||<xref:System.Int32>|32-bit işaretli tamsayı.|**tamsayı**|**int**|**int**<br /><br /> veya<br /><br /> **long**|**int**|  
||<xref:System.Int64>|64-bit imzalı bir tamsayı.|**uzun**|**long**|**__int64**|**int64**|  
||<xref:System.UInt16>|Bir 16 bitlik işaretsiz tamsayı.<br /><br /> CLS uyumlu değil.|**UShort**|**ushort**|**İmzasız short**|**uint16**|  
||<xref:System.UInt32>|32-bit işaretsiz bir tamsayı.<br /><br /> CLS uyumlu değil.|**Uınteger**|**uint**|**işaretsiz int**<br /> veya<br /> **İmzasız long**|**uint32**|  
||<xref:System.UInt64>|64-bit işaretsiz bir tamsayı.<br /><br /> CLS uyumlu değil.|**ULong**|**ulong**|**imzalanmamış __int64**|**uint64**|  
|Kayan nokta|<xref:System.Single>|Bir tek duyarlıklı (32-bit) kayan noktalı sayı.|**Tek**|**float**|**float**|**float32**</br> veya</br>**single**|  
||<xref:System.Double>|Bir çift duyarlıklı (64-bit) kayan noktalı sayı.|**çift**|**double**|**double**|**float**</br> veya </br> **double**|  
|Mantıksal|<xref:System.Boolean>|Bir Boole değeri (true veya false).|**Boole değeri**|**bool**|**bool**|**bool**|  
|Diğer|<xref:System.Char>|Unicode (16-bit) karakter.|**Char**|**char**|**wchar_t**|**char**|  
||<xref:System.Decimal>|Ondalık (128-bit) bir değer.|**Ondalık**|**decimal**|**Ondalık**|**decimal**|  
||<xref:System.IntPtr>|Temel alınan Platformu (32-bit platformlarda bir 32-bit değeri) ve 64-bit değeri bir 64-bit platformlarda boyutu bağımlı bir işaretli tamsayı.|**IntPtr**<br /><br /> Yerleşik tür yok.|**IntPtr**<br /><br /> Yerleşik tür yok.|**IntPtr**<br /><br /> Yerleşik tür yok.|**unativeint**|  
||<xref:System.UIntPtr>|Temel alınan Platformu (32-bit platformlarda bir 32-bit değeri) ve 64-bit değeri bir 64-bit platformlarda boyutu bağlıdır, işaretsiz bir tamsayı.<br /><br /> CLS uyumlu değil.|**UIntPtr**<br /><br /> Yerleşik tür yok.|**UIntPtr**<br /><br /> Yerleşik tür yok.|**UIntPtr**<br /><br /> Yerleşik tür yok.|**unativeint**|  
||<xref:System.Object>|Nesne hiyerarşisi kökü.|**Nesne**|**object**|**Nesne ^**|**obj**|  
||<xref:System.String>|Unicode karakterden oluşan bir sabit, sabit uzunluklu dize.|**dize**|**string**|**String ^**|**string**|  
  
 Temel veri türlerinin yanı sıra <xref:System> ad alanı, uygulama etki alanları ve atık toplayıcı gibi temel çalışma zamanı kavramları uğraşmanız sınıfları için özel durumları işlemek sınıflar arasında değişen 100'den fazla sınıflar içerir. <xref:System> Ad alanında ayrıca birçok ikinci düzey ad alanları bulunur.  
  
 Ad alanları hakkında daha fazla bilgi için [.NET API Browser](https://docs.microsoft.com/dotnet/api) .NET sınıf kitaplığı gidin. API başvuru belgeleri, her ad alanı, kendi türleri ve her üye üzerinde belgeler sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ortak Tür Sistemi](../../docs/standard/base-types/common-type-system.md)  
- [.NET API tarayıcısı](https://docs.microsoft.com/dotnet/api)  
- [Genel bakış](../../docs/framework/get-started/overview.md)
