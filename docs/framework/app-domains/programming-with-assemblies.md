---
title: Derlemelerle Programlama
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 368021062a3ad49d2c63f92797c59b8c0f1cddfc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="programming-with-assemblies"></a>Derlemelerle Programlama
Derlemeler, .NET Framework'ün yapı taşlarıdır; Bunlar, dağıtım, sürüm denetimi, yeniden, etkinleştirme kapsamı ve güvenlik izinleri temel birimini oluşturur. Bir derleme, ortak dil çalışma zamanına tür uygulamalarına dikkat etmesi için gerekli bilgileri sunar. Türleri ve birlikte çalışır ve işlevlerin bir mantıksal birim oluşturmak için yerleşik kaynakların bir koleksiyonudur. Çalışma zamanı için, bir derleme bağlamı dışında bir tür yoktur.  
  
 Bu bölümde, modülleri oluşturma, modüllerden derlemeleri oluşturma, bir anahtar çifti oluşturma ve bir derlemeyi tanımlayıcı adla imzalama ve bir derlemeyi genel derleme önbelleğine yükleme açıklar. Ayrıca, bu bölümde nasıl kullanılacağını açıklar [MSIL ayrıştırıcı (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) derleme bildirimi bilgilerini görüntülemek için.  
  
> [!NOTE]
>  .NET Framework sürüm 2.0 ile başlayarak, çalışma zamanı şu anda yüklenen çalışma zamanı'den daha yüksek bir sürüm numarası .NET Framework sürümü için derlenmiş bir derlemeyi yüklemez. Bu sürüm numarası birincil ve ikincil bileşenlerinin birleşimi için geçerlidir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Derlemeleri oluşturma](../../../docs/framework/app-domains/create-assemblies.md)  
 Tek dosya ve birden çok dosya derlemeleri genel bir bakış sağlar.  
  
 [Derleme adları](../../../docs/framework/app-domains/assembly-names.md)  
 Adlandırma derleme genel bir bakış sağlar.  
  
 [Nasıl yapılır: bir derlemenin tam olarak nitelenmiş adını belirleme](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
 Derleme tam olarak nitelenmiş adını belirlemek açıklar.  
  
 [Tam güvende Intranet uygulamalarını çalıştırma](../../../docs/framework/app-domains/running-intranet-applications-in-full-trust.md)  
 Bir intranet paylaşımında tam güven derlemeler için eski güvenlik ilkesini belirtmek açıklar.  
  
 [Derleme konumu](../../../docs/framework/app-domains/assembly-location.md)  
 Derlemeleri yerleştireceğinizi genel bir bakış sağlar.  
  
 [Nasıl yapılır: tek dosyalı derleme oluşturma](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 Tek Dosyalı derleme oluşturmayı açıklar.  
  
 [Birden çok dosya derlemeleri](../../../docs/framework/app-domains/multifile-assemblies.md)  
 Birden çok dosya derlemeleri oluşturma nedenleri açıklanmaktadır.  
  
 [Nasıl yapılır: birden fazla dosya derleme](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 Birden fazla dosya derlemesi oluşturmayı açıklar.  
  
 [Derleme özniteliklerini ayarlama](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 Derleme özniteliklerinin ve bunları nasıl ayarlayacağınız açıklanmaktadır.  
  
 [Oluşturma ve tanımlayıcı adlı derlemeler kullanma](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 Neden ve nasıl bir derlemeyi tanımlayıcı adla oturum açıklar ve nasıl yapılır konuları içerir.  
  
 [Derleme imzalamayı geciktirme](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 Açıklar nasıl geciktirin bütünleştirilmiş yapılır.  
  
 [Derlemeler ve genel derleme önbelleği ile çalışma](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 Neden ve nasıl derlemeleri genel derleme önbelleğine ekleme açıklar ve nasıl yapılır konuları içerir.  
  
 [Nasıl yapılır: derleme içeriklerini görüntüleme](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 MSIL ayrıştırıcı (Ildasm.exe) derleme içeriğini görüntülemek için nasıl kullanılacağını açıklar.  
  
 [Ortak dil çalışma zamanı tür iletme](../../../docs/framework/app-domains/type-forwarding-in-the-common-language-runtime.md)  
 Tür iletme uygulamalarınız bozmadan bir türü farklı bir derlemeye taşımak için nasıl kullanılacağını açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Reflection.Assembly>  
 Bir derlemeyi temsil eden .NET Framework sınıf.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Nasıl yapılır: bir derlemeden tür ve üye bilgilerini alın](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 Program aracılığıyla bir derlemeden tür ve diğer bilgileri elde etmek açıklar.  
  
 [Ortak dil çalışma zamanı derlemeleri](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Kavramsal genel bakış ortak dil çalışma zamanı derlemeleri sağlar.  
  
 [Derleme sürümü oluşturma](../../../docs/framework/app-domains/assembly-versioning.md)  
 Derleme bağlama'nin ve bir genel bakış sunulmaktadır <xref:System.Reflection.AssemblyVersionAttribute> ve <xref:System.Reflection.AssemblyInformationalVersionAttribute> öznitelikleri.  
  
 [Çalışma zamanı derlemeleri nasıl bulur](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 Çalışma zamanı bağlama isteği yerine getirmek için kullanılacak hangi derleme nasıl belirlediğini açıklar.  
  
 [Yansıma](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Nasıl kullanılacağını açıklar **yansıma** derleme hakkında bilgi edinmek için sınıf.
