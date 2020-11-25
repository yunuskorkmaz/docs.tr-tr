---
title: İntranet Uygulamalarını Tam Güvende Çalıştırma
description: Intranet uygulamalarını .NET Framework 3,5 SP1 ile tam güvende çalıştırın. Uygulamalar ve kitaplık derlemeleri bir ağ paylaşımından tam güvenli derlemeler olarak çalıştırılabilir.
ms.date: 03/30/2017
helpviewer_keywords:
- full trust, running intranet applications in
- intranet applications, running in full trust
- running intranet applications in full trust
ms.assetid: ee13c0a8-ab02-49f7-b8fb-9eab16c6c4f0
ms.openlocfilehash: 01d98a1ca7ce67088b4f04bedf7e3ef02e0ca7a5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723720"
---
# <a name="running-intranet-applications-in-full-trust"></a>İntranet Uygulamalarını Tam Güvende Çalıştırma

.NET Framework sürüm 3,5 hizmet paketi 1 ' den (SP1) başlayarak, uygulamalar ve kitaplık derlemeleri bir ağ paylaşımından tam güvenli derlemeler olarak çalıştırılabilir. <xref:System.Security.SecurityZone.MyComputer> bölge kanıtı, intranetteki bir paylaşımdan yüklenen derlemelere otomatik olarak eklenir. Bu kanıt, bu derlemelere, bilgisayarda bulunan Derlemelerle aynı izin kümesini (genellikle tam güven) verir. Bu işlev ClickOnce uygulamaları veya bir konakta çalışmak üzere tasarlanan uygulamalar için geçerlidir.

## <a name="rules-for-library-assemblies"></a>Kitaplık derlemeleri için kurallar

Bir ağ paylaşımında yürütülebilir dosya tarafından yüklenen derlemeler için aşağıdaki kurallar geçerlidir:

- Kitaplık derlemeleri yürütülebilir derlemeyle aynı klasörde bulunmalıdır. Bir alt klasörde bulunan veya farklı bir yolda başvurulan derlemelere tam güven izin kümesi verilmez.

- Yürütülebilir dosya bir derlemeyi yüklerse, yürütülebilir dosyayı başlatmak için kullanılan yolun aynısını kullanması gerekir. Örneğin, \\ \\ *ağ-bilgisayar* \\ *paylaşımının* paylaşılması bir sürücü harfine eşlenmişse ve çalıştırılabilir dosya bu yoldan çalıştırıldıysanız, ağ yolu kullanılarak yürütülebilir dosya tarafından yüklenen derlemelere tam güven verilmeyecektir. Bölgedeki bir derlemeyi geciktirmek için <xref:System.Security.SecurityZone.MyComputer> yürütülebilir dosyanın sürücü harfi yolunu kullanması gerekir.

## <a name="restoring-the-former-intranet-policy"></a>Eski Intranet Ilkesini geri yükleme

.NET Framework önceki sürümlerinde, paylaşılan derlemelere <xref:System.Security.SecurityZone.Intranet> bölge kanıtı verildi. Bir paylaşımdaki derlemeye tam güven sağlamak için kod erişimi güvenlik ilkesi belirtmeniz gerekiyordu.

Bu yeni davranış, intranet derlemeleri için varsayılandır. <xref:System.Security.SecurityZone.Intranet>Bilgisayardaki tüm uygulamalar için geçerli olan bir kayıt defteri anahtarı ayarlayarak kanıt sağlamaya yönelik önceki davranışa dönebilirsiniz. Bu işlem 32-bit ve 64 bit bilgisayarlar için farklıdır:

- 32 bit bilgisayarlarda, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoftaltında bir alt anahtar oluşturun \\ . Sistem kayıt defterindeki NETFramework anahtarı. Bir DWORD değeri 1 olan LegacyMyComputerZone anahtar adını kullanın.

- 64 bit bilgisayarlarda, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoftaltında bir alt anahtar oluşturun \\ . Sistem kayıt defterindeki NETFramework anahtarı. Bir DWORD değeri 1 olan LegacyMyComputerZone anahtar adını kullanın. HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoftaltında aynı alt anahtarı oluşturun \\ . NETFramework anahtarı.

## <a name="see-also"></a>Ayrıca bkz.

- [Derlemelerle Programlama](../../standard/assembly/index.md)
