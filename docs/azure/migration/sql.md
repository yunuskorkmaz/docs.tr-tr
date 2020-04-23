---
title: Azure’a SQL Server veritabanını geçirme
description: Bir SQL Server veritabanını şirket içi SQL Server'dan Azure'a nasıl geçirebilirsiniz öğrenin.
ms.topic: how-to
ms.date: 11/15/2017
ms.openlocfilehash: dac35970f2d77e232c2ee1a5e3a1f6e7bfec2317
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2020
ms.locfileid: "82072097"
---
# <a name="migrate-a-sql-server-database-to-azure"></a>Azure’a SQL Server veritabanını geçirme

Bu kısa makale, bir SQL Server veritabanını Azure'a geçirmek için iki seçeneğin kısa bir özetini sağlar.

Azure'un üretim SQL Server veritabanını geçirmek için iki birincil seçeneği vardır:

1. [Azure Sanal M'lerde SQL Server](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-iaas-overview): Azure'da çalışan bir Windows Sanal Makinesi'nde yüklü ve barındırılan ve Hizmet Olarak Altyapı (IaaS) olarak da bilinen bir SQL Server örneği.
2. [Azure SQL Veritabanı](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview): Hizmet Olarak Platform (PaaS) olarak da bilinen tam olarak yönetilen bir SQL veritabanı Azure hizmetidir.

Her ikisi de geçiş yapmadan önce değerlendirmeniz gereken artıları ve eksileri ile birlikte gelir.

## <a name="get-started"></a>başlarken

Kullandığınız hizmete bağlı olarak aşağıdaki geçiş kılavuzları yararlı olacaktır:

* [Bir SQL Server veritabanını Azure VM’deki SQL Server’a geçirme](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-migrate-sql)
* [SQL Server veritabanınızı Azure SQL Veritabanına geçirme](https://docs.microsoft.com/azure/sql-database/sql-database-migrate-your-sql-server-database)

Ayrıca, kavramsal içeriğe aşağıdaki bağlantılar VM'leri daha iyi anlamanıza yardımcı olur:

* [Azure Sanal Makineler’de SQL Server için yüksek kullanılabilirlik ve olağanüstü durum kurtarma](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-high-availability-dr)
* [Azure Sanal Makinelerde SQL Server için performansa yönelik en iyi yöntemler](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-performance)
* [Azure Sanal Makineler'de SQL Server için Uygulama Desenleri ve Geliştirme Stratejileri](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-app-patterns-dev-strategies)

Aşağıdaki bağlantılar Azure SQL Veritabanı'nı daha iyi anlamanıza yardımcı olur:

* [Azure SQL Veritabanı sunucuları ve veritabanları oluşturma ve yönetme](https://docs.microsoft.com/azure/sql-database/sql-database-servers-databases)
* [Veritabanı İşlem Birimleri (DTS) ve elastik Veritabanı İşlem Birimleri (eDTUs)](https://docs.microsoft.com/azure/sql-database/sql-database-what-is-a-dtu)
* [Azure SQL Veritabanı kaynak sınırları](https://docs.microsoft.com/azure/sql-database/sql-database-resource-limits)

## <a name="choosing-iaas-or-paas"></a>IaaS veya PaaS seçimi

Veritabanınızı nereye geçirebileceğinizi değerlendirirken, IaaS veya PaaS'ın sizin için daha uygun olup olmadığını belirleyin.

**Şunları varsa Azure VM'lerde SQL Server'ı seçin:**

* Veritabanınızı ve uygulamalarınızı en az değişiklik olmadan "kaldırma ve kaydırma" arayışındasınız.
* Veritabanı sunucunuz ve üzerinde çalıştığı VM üzerinde tam denetime sahip olmayı tercih edersiniz.
* Zaten kullanmak istediğiniz SQL Server ve Windows Server lisanslarınız vardır.

**Azure SQL Veritabanı'i aşağıdaki koşullar geçerli olduğunda tercih edin:**

* Uygulamalarınızı modernize etmek istiyorsanız, Azure'daki diğer PaaS hizmetlerini kullanmak için geçiş yapıyorsunuz.
* Veritabanı sunucunuzu ve üzerinde çalıştığı VM'yi yönetmek istemezsiniz.
* SQL Server veya Windows Server lisanslarınız yok veya lisansların süresinin dolmasına izin vermek niyetindesiniz.

Aşağıdaki tabloda, her hizmet arasındaki farklar bir dizi senaryoya göre açıklanmaktadır.

| Senaryo | Azure VM'lerde SQL Server | Azure SQL Veritabanı |
|----------|-------------------------|--------------------|
| Geçiş | Veritabanınızda en az değişiklik gerektirir. | [Veri Geçişi Yardımcısı](https://www.microsoft.com/download/details.aspx?id=53595)tarafından belirlendiği gibi Azure SQL'de kullanılamayan özellikleri kullanıyorsanız veya yerel olarak yüklenmiş yürütülebilir ler gibi başka bağımlılıklarınız varsa veritabanınızda değişiklik yapılmasını gerektirebilir.|
| Kullanılabilirliği, kurtarmayı ve yükseltmeleri yönetme | Kullanılabilirlik ve kurtarma el ile yapılandırılır. Yükseltmeler [VM Ölçek Setleri](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade)ile otomatikhale alınabilir. | Otomatik olarak sizin için yönetilir. |
| Temel işletim sistemi yapılandırması | Manuel yapılandırma. | Otomatik olarak sizin için yönetilir. |
| Veritabanı boyutunu yönetme | SQL Server örneğine göre 64 TB'a kadar depolama yı destekler. | Yatay bir bölüme ihtiyaç duymadan önce 4 TB depolama yı destekler. |
| Maliyetleri yönetme | SQL Server lisans maliyetlerini, Windows Server lisans maliyetlerini ve VM maliyetlerini (çekirdek, RAM ve depolamaya dayalı) yönetmeniz gerekir. | Servis maliyetlerini (elastik bir havuz kullanıyorsanız [eCD veya DT'lere,](https://docs.microsoft.com/azure/sql-database/sql-database-what-is-a-dtu)depolama alanına ve veritabanlarının sayısına göre) yönetmeniz gerekir. Ayrıca herhangi bir SLA maliyetini yönetmek gerekir. |

İkisi arasındaki farklar hakkında daha fazla bilgi edinmek için bulut SQL Server seçeneğini seçin: [Azure VM'lerde Azure SQL Veritabanı veya SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas)seçeneğini okuyun.

## <a name="faq"></a>SSS

* **Azure VM'lerde veya Azure SQL Veritabanı'nda SQL Server Server ile SQL Server Management Studio ve SQL Server Reporting Services (SSRS) gibi araçları kullanmaya devam edebilir miyim?**

    Evet! Tüm Microsoft SQL araçlama her iki hizmetile çalışır. Ancak SSRS, Azure SQL Veritabanı'nın bir parçası değildir ve azure vm'de çalıştırıp veritabanı örneğinize doğrultmanız önerilir.

* **PaaS'a gitmek istiyorum ama veritabanımın uyumlu olup olmadığından emin değilim. Yardım etmek için araçlar var mı?**

    Evet. [Veri Geçişi Yardımcısı,](https://www.microsoft.com/download/details.aspx?id=53595) Azure SQL Veritabanı'na geçişin bir parçası olarak kullanılan bir araçtır. [Azure Veritabanı Geçiş Hizmeti,](https://azure.microsoft.com/campaigns/database-migration/) IaaS veya PaaS için kullanabileceğiniz bir önizleme hizmetidir.

* **Maliyetleri tahmin edebilir miyim?**

    Evet. [Azure Fiyatlandırma Hesaplayıcısı,](https://azure.microsoft.com/pricing/calculator/) VM'ler ve veritabanı hizmetleri de dahil olmak üzere tüm Azure hizmetlerinin maliyetlerini tahmin etmek için kullanılabilir.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Doğru Azure barındırma seçeneğini seçin](choose.md)
