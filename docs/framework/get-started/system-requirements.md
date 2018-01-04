---
title: .NET framework sistem gereksinimleri
ms.custom: updateeachrelease
ms.date: 10/17/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords:
- software requirements
- .NET Framework, system requirements
- system requirements
- operating systems supported
- hardware requirements
ms.assetid: 298275e2-da1d-4618-9f74-6a3567832350
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f206dd52f5fd6dc114ea35ce22df05e0fcff956c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="net-framework-system-requirements"></a>.NET framework sistem gereksinimleri

Bu konudaki tablolar donanım, işletim sistemi ve .NET Framework 4.5 ve onun noktası sürümleri (4.5.1 ve 4.5.2) için yazılım gereksinimleri sağlar [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] (4.6.1 ve 4.6.2), kendi noktası sürümleri ve .NET Framework 4.7 ve kendi noktası Yayın (4.7.1). .NET Framework uygulamaları geliştirmek etkinleştirmeniz geliştirme ortamlarını ayrı dizi gereksinim mevcuttur.

İndirme bilgileri ve bağlantılar için bkz: [geliştiriciler için .NET Framework'ü yüklemek](../../../docs/framework/install/guide-for-developers.md).

.NET Framework sürüm desteği yaşam döngüsü hakkında daha fazla bilgi için bkz: [Microsoft destek yaşam döngüsü](https://support.microsoft.com/en-us/lifecycle/search?sort=PN&alpha=Microsoft%20.NET%20Framework&Filter=FilterNO).

## <a name="hardware-requirements"></a>Donanım gereksinimleri

|                          |        |
| ------------------------ | ------ |
| **İşlemci**            | 1 GHz  |
| **RAM**                  | 512 MB |
| **Disk alanı (en az)** |        |
| 32 bit:                   | 4.5 GB |
| 64 bit                   | 4.5 GB |

## <a name="installation-requirements"></a>Yükleme gereksinimleri

.NET Framework yükleme için yönetici ayrıcalıkları gerektirir. Burada .NET Framework'ü yüklemek istediğiniz bilgisayarda yönetici haklarına sahip değilseniz, ağ yöneticinize başvurun.

## <a name="supported-client-operating-systems"></a>Desteklenen istemci işletim sistemleri

| İşletim sistemi | Desteklenen sürümler | İşletim sistemi ile önceden yüklenmiş | Yüklenebilir ayrı olarak |
| ---------------- | ------------------ | ------------------------ | ---------------------- |
| Windows 10 sonbaharda oluşturucuları güncelleştir | 32 bit ve 64 bit | .NET framework 4.7.1 | |
| Windows 10 oluşturucuları güncelleştir | 32 bit ve 64 bit | .NET framework 4.7 | .NET framework 4.7.1 | 
| Windows 10 Yıldönümü Güncelleştirmesi | 32 bit ve 64 bit | [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]|.NET framework 4.7<br/><br/>.NET framework 4.7.1 |
| Windows 10 Kasım güncelleştirme | 32 bit ve 64 bit | .NET Framework 4.6.1 | .NET Framework 4.6.2 |
| Windows 10 | 32 bit ve 64 bit | .NET Framework 4.6 | .NET Framework 4.6.1 <br/><br/> .NET Framework 4.6.2 |
| [!INCLUDE[win81](../../../includes/win81-md.md)] | 32-bit, 64 bit ve ARM | [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] | [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<br /><br /> [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]<br /><br />.NET framework 4.7<br/><br/>.NET framework 4.7.1 |
| [!INCLUDE[win8](../../../includes/win8-md.md)] | 32-bit, 64 bit ve ARM | [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] | [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] |
| Windows 7 SP1|32 bit ve 64 bit | -- | .NET Framework 4<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<br /><br /> [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]<br /><br />.NET framework 4.7<br/><br/>.NET framework 4.7.1|
| Windows Vista SP2|32 bit ve 64 bit | -- | .NET Framework 4<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] |
| Windows XP |32 bit ve 64 bit | -- | .NET Framework 4 |

 **Notlar:**

- Windows 7 sistemlerde, Windows 7 SP1 .NET Framework gerektirir. Windows 7'de yaptığınız ve henüz Service Pack 1 yüklü olmayan, .NET Framework yüklemeden önce yapmanız gerekir.

- [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Windows Önyükleme Ortamı (Windows PE) desteklenir. Windows PE'de tüm özellikler desteklenir.

- .NET Framework 4, IA64 platformu da destekler.

- Tüm platformlar için en son Windows hizmet paketine yükseltin ve kullanılabilir kritik güncelleştirmeleri yükleyin öneririz [Windows Update Web sitesini](http://go.microsoft.com/fwlink/?LinkId=168461) en iyi uyumluluk ve güvenliği sağlamak için.

- 64-bit işletim sistemlerinde, .NET Framework WOW64 (32-bit bir 64-bit makinede işleme) ve yerel 64 bit işlem destekler.

## <a name="supported-server-operating-systems"></a>Desteklenen sunucu işletim sistemleri

| İşletim sistemi | Desteklenen sürümler | İşletim sistemi ile önceden yüklenmiş | Yüklenebilir ayrı olarak |
| ---------------- | ------------------ | ------------------------ | ---------------------- |
| Windows Server, sürüm 1709 | 64 bit | .NET framework 4.7.1 | -- |
| Windows Server 2016 | 64 bit | [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] | .NET framework 4.7<br/><br/> .NET framework 4.7.1 |
| Windows Server 2012 R2 | 64 bit | [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] | [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<br /><br /> [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]<br /><br />.NET framework 4.7<br/><br/> .NET framework 4.7.1 |
| Windows Server 2012 (64-bit edition) | 64 bit| [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] | [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<br /><br /> [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]<br /><br />.NET framework 4.7<br/><br/>.NET framework 4.7.1 |
| Windows Server 2008 R2 SP1|64 bit | -- | .NET Framework 4<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<br /><br /> [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]<br /><br />.NET framework 4.7<br/><br/>.NET framework 4.7.1 |
| Windows Server 2008 SP2|32 bit ve 64 bit | -- | .NET Framework 4<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] |

 **Notlar:**

- [!INCLUDE[winserver8](../../../includes/winserver8-md.md)]içeren [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], böylece ayrı olarak yüklemeniz gerekmez. Benzer şekilde, [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)] içeren [!INCLUDE[net_v451](../../../includes/net-v451-md.md)].

- .NET Framework Sunucu Çekirdeği rolü Windows Server 2008 R2 SP1 veya sonraki sürümü için destek sınırlıdır. Bkz: [Sunucu Çekirdek .NET işlevlerini](https://msdn.microsoft.com/library/ee391632.aspx) desteklenmeyen API'leri listesi.

- .NET Framework Itanium tabanlı sistemler için Windows Server 2008 R2'de desteklenmez.

- Windows Server 2008 SP2, Sunucu Çekirdeği rolü, .NET Framework desteklenmiyor.

- Tüm platformlar için en son Windows hizmet paketine yükseltin ve kritik kullanılabilir güncelleştirmeler öneririz [Windows Update Web sitesini](http://go.microsoft.com/fwlink/?LinkId=168461) en iyi uyumluluk ve güvenliği sağlamak için. En son Windows hizmet paketi yüklemesini bazı işletim sistemlerinde gerekebilir.

- 64-bit işletim sistemlerinde, .NET Framework WOW64 (32-bit bir 64-bit makinede işleme) ve yerel 64 bit işlem destekler.

## <a name="see-also"></a>Ayrıca bkz.

[Yükleme Kılavuzu](../../../docs/framework/install/index.md)   
[Başlarken](../../../docs/framework/get-started/index.md)   
[Engellenen .NET Framework yükleme ve kaldırma sorunlarını giderme](../../../docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)
