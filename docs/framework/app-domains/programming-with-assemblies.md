---
title: Derlemelerle Programlama
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f427e2260fb26be7db0a29c47f38a3cb32dd34e9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921427"
---
# <a name="programming-with-assemblies"></a>Derlemelerle Programlama
Derlemeler .NET Framework yapı taşlarıdır; temel dağıtım, sürüm denetimi, yeniden kullanım, etkinleştirme kapsamı ve güvenlik izinleri oluşturur. Bir derleme, ortak dil çalışma zamanına tür uygulamalarına dikkat etmesi için gerekli bilgileri sunar. Birlikte çalışacak ve mantıksal bir işlevsellik birimi oluşturacak bir tür ve kaynak koleksiyonudur. Çalışma zamanı için, bir derleme bağlamı dışında bir tür yoktur.  
  
 Bu bölümde modüller oluşturma, modüllerden derlemeler oluşturma, bir anahtar çifti oluşturma ve bir derlemeyi tanımlayıcı adla imzalama ve genel bütünleştirilmiş kod önbelleğine bir derleme yüklemesi açıklanmaktadır. Ayrıca, bu bölümde, derleme bildirimi bilgilerini görüntülemek için [MSIL Disassembler (ıldadsm. exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) ' nin nasıl kullanılacağı açıklanmaktadır.  
  
> [!NOTE]
> .NET Framework sürüm 2,0 ' den başlayarak, çalışma zamanı, yüklü olan çalışma zamanından daha yüksek bir sürüm numarasına sahip .NET Framework bir sürümle derlenen bir derlemeyi yüklemez. Bu, sürüm numarasının büyük ve küçük bileşenlerinin birleşimi için geçerlidir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Bütünleştirilmiş Kodlar Oluşturma](../../../docs/framework/app-domains/create-assemblies.md)  
 Tek dosyalı ve çoklu dosya Derlemeleriyle genel bir bakış sağlar.  
  
 [Bütünleştirilmiş Kod Adları](../../../docs/framework/app-domains/assembly-names.md)  
 Derleme adlandırmasına genel bir bakış sağlar.  
  
 [Nasıl yapılır: Bir derlemenin tam nitelikli adını belirleme](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
 Bir derlemenin tam nitelikli adının nasıl belirleneceğini açıklar.  
  
 [Tam Güvende İntranet Uygulamalarını Çalıştırma](../../../docs/framework/app-domains/running-intranet-applications-in-full-trust.md)  
 Bir intranet paylaşımında tam güvenle derlemeler için eski güvenlik ilkesinin nasıl belirtileceğini açıklar.  
  
 [Bütünleştirilmiş Kod Konumu](../../../docs/framework/app-domains/assembly-location.md)  
 Derlemelerin nereye bulunacağı hakkında genel bakış sağlar.  
  
 [Nasıl yapılır: Tek dosya derlemesi oluşturma](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 Tek dosya derlemesinin nasıl oluşturulacağını açıklar.  
  
 [Çok Dosyalı Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/multifile-assemblies.md)  
 Çok dosyalı derlemeler oluşturma nedenlerini açıklar.  
  
 [Nasıl yapılır: Çoklu dosya derlemesi oluşturma](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 Çoklu dosya derlemesinin nasıl oluşturulacağını açıklar.  
  
 [Bütünleştirilmiş Kod Özniteliklerini Ayarlama](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 Derleme özniteliklerini ve bunların nasıl ayarlanacağını açıklar.  
  
 [Kesin Adlandırılmış Bütünleştirilmiş Kodlar Oluşturma ve Kullanma](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 Bir derlemeyi güçlü bir adla nasıl ve neden imzalayabileceğinizi açıklar ve nasıl yapılır konularını içerir.  
  
 [Bütünleştirilmiş Kod İmzalamayı Geciktirme](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 Bir derlemenin nasıl geciktirileneceğini açıklar.  
  
 [Bütünleştirilmiş Kodlar ve Genel Derleme Önbelleği ile Çalışma](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 Derlemelerin nasıl ve neden genel derleme önbelleğine ekleneceğini ve nasıl yapılır konuları içerdiğini açıklar.  
  
 [Nasıl yapılır: Derleme Içeriğini görüntüle](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 Derleme içeriğini görüntülemek için MSIL Disassembler (ıldadsm. exe) ' nin nasıl kullanılacağını açıklar.  
  
 [Ortak Dil Çalışma Zamanı Modülünde Tür İletme](../../../docs/framework/app-domains/type-forwarding-in-the-common-language-runtime.md)  
 Mevcut uygulamaları bozmadan bir türü farklı bir derlemeye taşımak için tür iletmenin nasıl kullanılacağını açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Reflection.Assembly>  
 Bir derlemeyi temsil eden .NET Framework sınıfı.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Nasıl yapılır: Bir derlemeden tür ve üye bilgilerini alma](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 Bir derlemeden program aracılığıyla tür ve diğer bilgilerin nasıl elde edileceğini açıklar.  
  
 [Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Ortak dil çalışma zamanı derlemelerine kavramsal bir genel bakış sağlar.  
  
 [Bütünleştirilmiş Kod Sürümü Oluşturma](../../../docs/framework/app-domains/assembly-versioning.md)  
 Derleme bağlamaya ve <xref:System.Reflection.AssemblyVersionAttribute> ve <xref:System.Reflection.AssemblyInformationalVersionAttribute> özniteliklerine ilişkin bir genel bakış sağlar.  
  
 [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 Çalışma zamanının, bir bağlama isteğini yerine getirmek için hangi derlemeyi kullanacağınızı nasıl belirlediğini açıklar.  
  
 [Yansıma](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Bir derleme hakkında bilgi almak için **yansıma** sınıfının nasıl kullanılacağını açıklar.
