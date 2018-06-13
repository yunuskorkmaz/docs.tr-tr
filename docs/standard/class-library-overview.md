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
ms.openlocfilehash: c6c61e4721e6daa548db2fffccc75606e98f71cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33577312"
---
# <a name="net-class-library-overview"></a>.NET sınıf kitaplığına genel bakış
.NET uygulamaları, sınıflar, arabirimler, temsilciler ve hızlandırmak ve geliştirme sürecinin en iyi duruma getirme ve sistem işlevlere erişim sağlayan değer türleri içerir. Diller arasında birlikte çalışabilirlik kolaylaştırmak için çoğu .NET türleri CLS ile uyumlu olan ve bu nedenle, derleyici ortak dil belirtimi (CLS) uyan herhangi bir programlama dili kullanılabilir.  
  
 .NET, .NET uygulamaları, bileşenleri ve denetimleri yerleşiktir foundation türleridir. .NET uygulamaları aşağıdaki işlevleri gerçekleştirir türleri şunlardır:  
  
-   Temel veri türlerini ve özel durumları temsil eder.  
  
-   Veri yapıları kapsüller.  
  
-   G/ç gerçekleştirin.  
  
-   Yüklenen türler hakkında bilgi erişim.  
  
-   .NET Framework güvenlik denetimlerini çağırır.  
  
-   Veri erişimi, zengin istemci-tarafı GUI ve sunucu tarafından denetlenen, istemci-tarafı GUI sağlar.  
  
 .NET zengin bir soyut ve somut (soyut olmayan) sınıflar yanı sıra arabirimleri sağlar. Kendi sınıflarınızı aktarımlar, olduğu gibi veya pek çok durumda somut sınıflar kullanın. Arabirim işlevselliğini kullanmak için arabirimini uygulayan bir sınıf oluşturun veya arabirimini uygulayan .NET Framework sınıfları birinden bir sınıf türetin.  
  
## <a name="naming-conventions"></a>Adlandırma kuralları  
 .NET türleri bir hiyerarşi connotes nokta sözdizimini adlandırma şeması kullanın. Bunlar kullanılabilir aranır ve daha kolay başvurduğu için bu tekniği ad alanında ilgili türleri gruplandırır. Tam adı ilk bölümü — en sağdaki nokta kadar — ad alanı adı. Son adı tür adı parçasıdır. Örneğin, **System.Collections.ArrayList** temsil eden **ArrayList** ait olduğu tür **System.Collections** ad alanı. Türler **System.Collections** nesne koleksiyonları işlemek için kullanılabilir.  
  
 Bu adlandırma şeması genişletme kitaplığı geliştiriciler için kolaylaştırır [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] türleri hiyerarşik grupları oluşturmak ve bunları tutarlı ve bilgilendirici bir şekilde için. Ayrıca tam adına göre belirsizliğe tanımlanmasını türlerine izin verir (diğer bir deyişle, ad alanı ve tür adı), türü ad çakışmaları engeller. Aşağıdaki kural kendi ad alanları için adları oluşturulurken kullanılacak kitaplığı geliştiriciler bekleniyor:  
  
 *Şirket adı*. *TechnologyName*  
  
 Örneğin, ad alanı Microsoft.Word bu kılavuz için uygundur.  
  
 Grup için adlandırma modelleri kullanımını ad alanları türlerine oluşturmak ve belge sınıf kitaplıkları için çok kullanışlı bir yol ile ilgili. Ancak, bu adlandırma şeması görünürlük, üye erişimi, devralma, güvenlik veya bağlama üzerinde hiçbir etkisi yoktur. Bir ad alanı arasında birden çok derleme bölümlenebilir ve tek bir derleme birden çok ad alanını türlerinden içerebilir. Derleme sürümü oluşturma, dağıtım, güvenlik, yükleme ve ortak dil çalışma zamanı görünürlüğü resmi yapısı sağlar.  
  
 Ad alanları ve tür adları hakkında daha fazla bilgi için bkz: [ortak tür sistemi](../../docs/standard/base-types/common-type-system.md).  
  
## <a name="system-namespace"></a>Sistem Namespace  
 <xref:System> Ad .NET temel türleri için kök ad alanıdır. Bu ad alanı, tüm uygulamaları tarafından kullanılan temel veri türlerini temsil eden sınıflar içerir: <xref:System.Object> (devralma hiyerarşisi kökündeki) <xref:System.Byte>, <xref:System.Char>, <xref:System.Array>, <xref:System.Int32>, <xref:System.String>ve benzeri. Bu tür pek çok programlama diliniz kullanan temel veri türleri karşılık gelir. .NET Framework türleri kullanarak kod yazarken dilinizi ait karşılık gelen anahtar sözcüğü bir .NET Framework temel veri türü beklenen zaman kullanabilirsiniz.  
  
 Aşağıdaki tabloda .NET sağlar, kısaca her türünü tanımlar ve Visual Basic, C#, C++ ve F # içinde karşılık gelen türünü gösterir, temel türleri listelenmektedir.  
  
|Kategori|Sınıf adı|Açıklama|Visual Basic veri türü|C# veri türü|C + +/ CLI veri türü|F # veri türü|  
|--------------|----------------|-----------------|----------------------------|-------------------|---------------------|-----------------------|  
|Tamsayı|<xref:System.Byte>|Bir 8 bit işaretsiz tamsayıyı.|**Bayt**|**byte**|**İmzasız char**|**byte**|  
||<xref:System.SByte>|Bir 8 bit işaretli tamsayıyı.<br /><br /> Değil CLS ile uyumlu.|**SByte**|**sbyte**|**char**<br /> -veya-<br /> **İmzalı** **char**|**sbyte**|  
||<xref:System.Int16>|Bir 16 bit işaretli tamsayıyı.|**kısa**|**short**|**short**|**Int16**|  
||<xref:System.Int32>|32 bit imzalı bir tamsayı.|**tamsayı**|**int**|**int**<br /><br /> -veya-<br /><br /> **long**|**int**|  
||<xref:System.Int64>|64-bit imzalı bir tamsayı.|**uzun**|**long**|**__int64**|**int64**|  
||<xref:System.UInt16>|Bir 16 bit işaretsiz tamsayı.<br /><br /> Değil CLS ile uyumlu.|**UShort**|**ushort**|**İmzasız short**|**uint16**|  
||<xref:System.UInt32>|Bir 32 bit işaretsiz tamsayı.<br /><br /> Değil CLS ile uyumlu.|**Uınteger**|**uint**|**İmzasız int**<br /> -veya-<br /> **İmzasız long**|**uint32**|  
||<xref:System.UInt64>|Bir 64-bit işaretsiz tamsayı.<br /><br /> Değil CLS ile uyumlu.|**ULong**|**ulong**|**İmzasız __int64**|**uint64**|  
|Kayan nokta|<xref:System.Single>|Bir tek duyarlıklı (32 bit) kayan noktalı sayı.|**Tek**|**float**|**float**|**Float32**</br> veya</br>**single**|  
||<xref:System.Double>|Bir çift duyarlıklı (64 bit) kayan noktalı sayı.|**Çift**|**double**|**double**|**float**</br> veya </br> **double**|  
|Mantıksal|<xref:System.Boolean>|Bir Boole değeri (true veya false).|**Boole değeri**|**bool**|**bool**|**bool**|  
|Diğer|<xref:System.Char>|Unicode (16-bit) karakter.|**char**|**char**|**wchar_t**|**char**|  
||<xref:System.Decimal>|Ondalık (128-bit) bir değer.|**Ondalık**|**decimal**|**Ondalık**|**decimal**|  
||<xref:System.IntPtr>|Temel alınan bir platform (32-bit değer 32-bit platformu üzerinde) ve bir 64-bit platformu üzerinde 64-bit değeri büyüklüğü bağlıdır imzalı bir tamsayı.|**IntPtr**<br /><br /> Yerleşik tür yok.|**IntPtr**<br /><br /> Yerleşik tür yok.|**IntPtr**<br /><br /> Yerleşik tür yok.|**unativeint**|  
||<xref:System.UIntPtr>|İmzalanmamış tamsayı temel platform (32-bit değer 32-bit platformu üzerinde) ve bir 64-bit platformu üzerinde 64-bit değeri büyüklüğü bağlıdır.<br /><br /> Değil CLS ile uyumlu.|**UIntPtr**<br /><br /> Yerleşik tür yok.|**UIntPtr**<br /><br /> Yerleşik tür yok.|**UIntPtr**<br /><br /> Yerleşik tür yok.|**unativeint**|  
||<xref:System.Object>|Nesne hiyerarşisinin kökü.|**Nesne**|**object**|**Nesne ^**|**obj**|  
||<xref:System.String>|Unicode karakterden oluşan bir değişmez, sabit uzunluklu dize.|**Dize**|**string**|**Dize ^**|**string**|  
  
 Temel veri türlerini yanı sıra <xref:System> ad alanı, uygulama etki alanları ve atık toplayıcı gibi temel çalışma zamanı kavramlar uğraşmanız sınıfları için özel durumları işleme sınıflar arasında değişen 100'den sınıfları içerir. <xref:System> Ad alanı da birçok ikinci düzey ad alanları içerir.  
  
 Ad alanları hakkında daha fazla bilgi için kullanmak [.NET API tarayıcı](https://docs.microsoft.com/dotnet/api) .NET sınıf kitaplığı gidin. API başvuru belgeleri, her ad alanı, kendi türleri ve her üye üzerinde belgeler sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ortak Tür Sistemi](../../docs/standard/base-types/common-type-system.md)  
 [.NET API tarayıcı](https://docs.microsoft.com/dotnet/api)  
 [Genel bakış](../../docs/framework/get-started/overview.md)
