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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705551"
---
# <a name="programming-with-assemblies"></a>Derlemelerle Programlama
Derlemeler .NET Framework'ün yapı taşlarıdır; Bunlar, dağıtım, sürüm denetimi, yeniden kullanma, aktivasyon kapsamı ve güvenlik izinleri temel birimini oluşturur. Bir derleme, ortak dil çalışma zamanına tür uygulamalarına dikkat etmesi için gerekli bilgileri sunar. Türleri ve birlikte çalışan ve mantıksal bir işlevsellik birimi oluşturacak biçimde oluşturulan kaynakların bir koleksiyonudur. Çalışma zamanı için, bir derleme bağlamı dışında bir tür yoktur.  
  
 Bu bölümde, modülleri oluşturabilir, modüllerden bütünleştirilmiş kodları oluşturma, bir anahtar çifti oluşturma ve derlemeyi bir katı adla imzalamak ve bir derlemeyi genel bütünleştirilmiş kod önbelleğine yüklemek açıklar. Ayrıca, bu bölümde nasıl kullanılacağını açıklar [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) derleme bildirimi bilgilerini görüntülemek için.  
  
> [!NOTE]
>  .NET Framework sürüm 2.0 ile başlayarak, çalışma zamanı şu anda yüklü çalışma zamanı daha yüksek bir sürüm numarasına sahip .NET Framework sürümü ile derlenen bütünleştirilmiş yüklemez. Bu sürüm numarasının büyük ve küçük bileşenleri birleşimi için geçerlidir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Bütünleştirilmiş Kodlar Oluşturma](../../../docs/framework/app-domains/create-assemblies.md)  
 Tek dosya ve çok dosyalı derlemeler genel bir bakış sağlar.  
  
 [Bütünleştirilmiş Kod Adları](../../../docs/framework/app-domains/assembly-names.md)  
 Derleme adlandırma genel bir bakış sağlar.  
  
 [Nasıl yapılır: Bir derlemenin tam olarak nitelenmiş adını belirleme](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
 Bir derlemenin tam adını belirlemek açıklar.  
  
 [Tam Güvende İntranet Uygulamalarını Çalıştırma](../../../docs/framework/app-domains/running-intranet-applications-in-full-trust.md)  
 Bir intranet paylaşımında tam güven derlemeleri için eski güvenlik ilkesini belirtin açıklar.  
  
 [Bütünleştirilmiş Kod Konumu](../../../docs/framework/app-domains/assembly-location.md)  
 Derlemeleri nerede genel bir bakış sağlar.  
  
 [Nasıl yapılır: Tek Dosyalı bütünleştirilmiş kod derleme](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 Tek dosyalı bir derlemenin nasıl oluşturulacağını açıklar.  
  
 [Çok Dosyalı Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/multifile-assemblies.md)  
 Birden çok dosya derlemeleri oluşturmak için nedenleri açıklanmaktadır.  
  
 [Nasıl yapılır: Bir çoklu dosya derlemesi oluşturun](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 Çok dosyalı bir derlemenin nasıl oluşturulacağını açıklar.  
  
 [Bütünleştirilmiş Kod Özniteliklerini Ayarlama](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 Derleme özniteliklerinin ve bunların nasıl ayarlanacağını açıklar.  
  
 [Kesin Adlandırılmış Bütünleştirilmiş Kodlar Oluşturma ve Kullanma](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 Neden ve nasıl bir derlemeyi katı bir adla imzalamak açıklar ve nasıl yapılır konuları içerir.  
  
 [Bütünleştirilmiş Kod İmzalamayı Geciktirme](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 Açıklayan nasıl bir derlemeyi Gecikmeli imzalayın.  
  
 [Bütünleştirilmiş Kodlar ve Genel Derleme Önbelleği ile Çalışma](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 Neden ve nasıl derlemeleri genel derleme önbelleğine ekleme açıklar ve nasıl yapılır konuları içerir.  
  
 [Nasıl yapılır: Derleme içeriği görüntüle](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 Derleme içerikleri görüntülemek için MSIL Disassembler (Ildasm.exe) kullanmayı açıklar.  
  
 [Ortak Dil Çalışma Zamanı Modülünde Tür İletme](../../../docs/framework/app-domains/type-forwarding-in-the-common-language-runtime.md)  
 Tür iletme mevcut uygulamaları bozmadan farklı bir derlemeye bir tür taşımak için nasıl kullanılacağını açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Reflection.Assembly>  
 .NET Framework sınıf bir bütünleştirilmiş kodu temsil eder.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Nasıl yapılır: Derlemeden tür ve üye bilgilerini alma](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 Program aracılığıyla bir derlemeden tür ve diğer bilgileri alma açıklar.  
  
 [Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Kavramsal genel bakış ortak dil çalışma zamanı derlemeleri sağlar.  
  
 [Bütünleştirilmiş Kod Sürümü Oluşturma](../../../docs/framework/app-domains/assembly-versioning.md)  
 Derleme bağlama'nin ve bir genel bakış sağlar <xref:System.Reflection.AssemblyVersionAttribute> ve <xref:System.Reflection.AssemblyInformationalVersionAttribute> öznitelikleri.  
  
 [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 Çalışma zamanının hangi derleme bağlama isteğini yerine getirmek için kullanılacak etiketleneceğini nasıl açıklar.  
  
 [Yansıma](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Nasıl kullanılacağını açıklar **yansıma** derleme hakkında bilgi edinmek için sınıf.
