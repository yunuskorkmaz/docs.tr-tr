---
title: Derlemelerle Programlama
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f6a20a2e678c10157fed7da6f5de9f3ffee0c9ad
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="programming-with-assemblies"></a>Derlemelerle Programlama
Derlemeler, .NET Framework'ün yapı taşlarıdır; Bunlar, dağıtım, sürüm denetimi, yeniden, etkinleştirme kapsamı ve güvenlik izinleri temel birimini oluşturur. Bir derleme, ortak dil çalışma zamanına tür uygulamalarına dikkat etmesi için gerekli bilgileri sunar. Türleri ve birlikte çalışır ve işlevlerin bir mantıksal birim oluşturmak için yerleşik kaynakların bir koleksiyonudur. Çalışma zamanı için, bir derleme bağlamı dışında bir tür yoktur.  
  
 Bu bölümde, modülleri oluşturma, modüllerden derlemeleri oluşturma, bir anahtar çifti oluşturma ve bir derlemeyi tanımlayıcı adla imzalama ve bir derlemeyi genel derleme önbelleğine yükleme açıklar. Ayrıca, bu bölümde nasıl kullanılacağını açıklar [MSIL ayrıştırıcı (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) derleme bildirimi bilgilerini görüntülemek için.  
  
> [!NOTE]
>  .NET Framework sürüm 2.0 ile başlayarak, çalışma zamanı şu anda yüklenen çalışma zamanı'den daha yüksek bir sürüm numarası .NET Framework sürümü için derlenmiş bir derlemeyi yüklemez. Bu sürüm numarası birincil ve ikincil bileşenlerinin birleşimi için geçerlidir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Bütünleştirilmiş Kodlar Oluşturma](../../../docs/framework/app-domains/create-assemblies.md)  
 Tek dosya ve birden çok dosya derlemeleri genel bir bakış sağlar.  
  
 [Bütünleştirilmiş Kod Adları](../../../docs/framework/app-domains/assembly-names.md)  
 Adlandırma derleme genel bir bakış sağlar.  
  
 [Nasıl yapılır: Bir Bütünleştirilmiş Kodun Tam Adını Belirleme](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
 Derleme tam olarak nitelenmiş adını belirlemek açıklar.  
  
 [Tam Güvende İntranet Uygulamalarını Çalıştırma](../../../docs/framework/app-domains/running-intranet-applications-in-full-trust.md)  
 Bir intranet paylaşımında tam güven derlemeler için eski güvenlik ilkesini belirtmek açıklar.  
  
 [Bütünleştirilmiş Kod Konumu](../../../docs/framework/app-domains/assembly-location.md)  
 Derlemeleri yerleştireceğinizi genel bir bakış sağlar.  
  
 [Nasıl yapılır: Tek Dosyalı Bütünleştirilmiş Kod Derleme](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 Tek Dosyalı derleme oluşturmayı açıklar.  
  
 [Çok Dosyalı Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/multifile-assemblies.md)  
 Birden çok dosya derlemeleri oluşturma nedenleri açıklanmaktadır.  
  
 [Nasıl yapılır: Çok Dosyalı Bütünleştirilmiş Kod Derleme](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 Birden fazla dosya derlemesi oluşturmayı açıklar.  
  
 [Bütünleştirilmiş Kod Özniteliklerini Ayarlama](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 Derleme özniteliklerinin ve bunları nasıl ayarlayacağınız açıklanmaktadır.  
  
 [Kesin Adlandırılmış Bütünleştirilmiş Kodlar Oluşturma ve Kullanma](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 Neden ve nasıl bir derlemeyi tanımlayıcı adla oturum açıklar ve nasıl yapılır konuları içerir.  
  
 [Bütünleştirilmiş Kod İmzalamayı Geciktirme](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 Açıklar nasıl geciktirin bütünleştirilmiş yapılır.  
  
 [Bütünleştirilmiş Kodlar ve Genel Derleme Önbelleği ile Çalışma](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 Neden ve nasıl derlemeleri genel derleme önbelleğine ekleme açıklar ve nasıl yapılır konuları içerir.  
  
 [Nasıl yapılır: Bütünleştirilmiş Kod İçeriklerini Görüntüleme](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 MSIL ayrıştırıcı (Ildasm.exe) derleme içeriğini görüntülemek için nasıl kullanılacağını açıklar.  
  
 [Ortak Dil Çalışma Zamanı Modülünde Tür İletme](../../../docs/framework/app-domains/type-forwarding-in-the-common-language-runtime.md)  
 Tür iletme uygulamalarınız bozmadan bir türü farklı bir derlemeye taşımak için nasıl kullanılacağını açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Reflection.Assembly>  
 Bir derlemeyi temsil eden .NET Framework sınıf.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Nasıl yapılır: Bir Bütünleştirilmiş Koddan Tür ve Üye Bilgilerini Alma](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 Program aracılığıyla bir derlemeden tür ve diğer bilgileri elde etmek açıklar.  
  
 [Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Kavramsal genel bakış ortak dil çalışma zamanı derlemeleri sağlar.  
  
 [Bütünleştirilmiş Kod Sürümü Oluşturma](../../../docs/framework/app-domains/assembly-versioning.md)  
 Derleme bağlama'nin ve bir genel bakış sunulmaktadır <xref:System.Reflection.AssemblyVersionAttribute> ve <xref:System.Reflection.AssemblyInformationalVersionAttribute> öznitelikleri.  
  
 [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 Çalışma zamanı bağlama isteği yerine getirmek için kullanılacak hangi derleme nasıl belirlediğini açıklar.  
  
 [Yansıma](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Nasıl kullanılacağını açıklar **yansıma** derleme hakkında bilgi edinmek için sınıf.
