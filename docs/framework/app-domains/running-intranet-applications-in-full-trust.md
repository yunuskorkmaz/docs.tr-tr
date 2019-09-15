---
title: İntranet Uygulamalarını Tam Güvende Çalıştırma
ms.date: 03/30/2017
helpviewer_keywords:
- full trust, running intranet applications in
- intranet applications, running in full trust
- running intranet applications in full trust
ms.assetid: ee13c0a8-ab02-49f7-b8fb-9eab16c6c4f0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1996c8b317bbfed6362c759a257cafef8400e919
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971907"
---
# <a name="running-intranet-applications-in-full-trust"></a>İntranet Uygulamalarını Tam Güvende Çalıştırma
.NET Framework sürüm 3,5 hizmet paketi 1 ' den (SP1) başlayarak, uygulamalar ve kitaplık derlemeleri bir ağ paylaşımından tam güvenli derlemeler olarak çalıştırılabilir. <xref:System.Security.SecurityZone.MyComputer>bölge kanıtı, intranetteki bir paylaşımdan yüklenen derlemelere otomatik olarak eklenir. Bu kanıt, bu derlemelere, bilgisayarda bulunan Derlemelerle aynı izin kümesini (genellikle tam güven) verir. Bu işlev ClickOnce uygulamaları veya bir konakta çalışmak üzere tasarlanan uygulamalar için geçerlidir.  
  
## <a name="rules-for-library-assemblies"></a>Kitaplık derlemeleri için kurallar  
 Bir ağ paylaşımında yürütülebilir dosya tarafından yüklenen derlemeler için aşağıdaki kurallar geçerlidir:  
  
- Kitaplık derlemeleri yürütülebilir derlemeyle aynı klasörde bulunmalıdır. Bir alt klasörde bulunan veya farklı bir yolda başvurulan derlemelere tam güven izin kümesi verilmez.  
  
- Yürütülebilir dosya bir derlemeyi yüklerse, yürütülebilir dosyayı başlatmak için kullanılan yolun aynısını kullanması gerekir. Örneğin, \\ *ağ-bilgisayar*\\*paylaşımının* paylaşılması \\bir sürücü harfine eşlenmişse ve çalıştırılabilir dosya bu yoldan çalışıyorsa, yürütülebilir dosya tarafından ağ yolu kullanılarak yüklenen derlemeler bu şekilde olmayacaktır tam güven verilmelidir. <xref:System.Security.SecurityZone.MyComputer> Bölgedeki bir derlemeyi geciktirmek için yürütülebilir dosyanın sürücü harfi yolunu kullanması gerekir.  
  
## <a name="restoring-the-former-intranet-policy"></a>Eski Intranet Ilkesini geri yükleme  
 .NET Framework önceki sürümlerinde, paylaşılan derlemelere bölge kanıtı verildi <xref:System.Security.SecurityZone.Intranet> . Bir paylaşımdaki derlemeye tam güven sağlamak için kod erişimi güvenlik ilkesi belirtmeniz gerekiyordu.  
  
 Bu yeni davranış, intranet derlemeleri için varsayılandır. Bilgisayardaki tüm uygulamalar için geçerli olan bir kayıt defteri <xref:System.Security.SecurityZone.Intranet> anahtarı ayarlayarak kanıt sağlamaya yönelik önceki davranışa dönebilirsiniz. Bu işlem 32-bit ve 64 bit bilgisayarlar için farklıdır:  
  
- 32 bit bilgisayarlarda, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\altında bir alt anahtar oluşturun. Sistem kayıt defterindeki NETFramework anahtarı. Bir DWORD değeri 1 olan LegacyMyComputerZone anahtar adını kullanın.  
  
- 64 bit bilgisayarlarda, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\altında bir alt anahtar oluşturun. Sistem kayıt defterindeki NETFramework anahtarı. Bir DWORD değeri 1 olan LegacyMyComputerZone anahtar adını kullanın. HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\altında aynı alt anahtarı oluşturun. NETFramework anahtarı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bütünleştirilmiş Kodlarla Programlama](../../standard/assembly/program.md)
