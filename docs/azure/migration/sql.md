---
title: Azure’a SQL Server veritabanını geçirme
description: SQL Server veritabanını şirket içi SQL Server Azure 'a geçirmeyi öğrenin.
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

Bu kısa makalede, SQL Server veritabanını Azure 'a geçirmek için iki seçenekten oluşan kısa bir ana hat sunulmaktadır.

Azure, bir üretim SQL Server veritabanının geçirilmesi için iki birincil seçeneğe sahiptir:

1. [Azure VM 'lerinde SQL Server](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-iaas-overview): Azure 'da çalışan ve hizmet olarak altyapı (IaaS) olarak da bilinen bir Windows sanal makinesinde yüklü ve barındırılan bir SQL Server örneği.
2. [Azure SQL veritabanı](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview): hizmet olarak platform (PaaS) olarak da bilinen, tam olarak YÖNETILEN bir SQL veritabanı Azure hizmetidir.

Her ikisi de, geçirmeden önce değerlendirmeniz gereken profesyonelleri ve dezavantajlarla birlikte gelir.

## <a name="get-started"></a>başlarken

Kullandığınız hizmete bağlı olarak aşağıdaki geçiş kılavuzlarınız yararlı olacaktır:

* [Bir SQL Server veritabanını Azure VM’deki SQL Server’a geçirme](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-migrate-sql)
* [SQL Server veritabanınızı Azure SQL Veritabanına geçirme](https://docs.microsoft.com/azure/sql-database/sql-database-migrate-your-sql-server-database)

Ayrıca, kavramsal içeriğe yönelik aşağıdaki bağlantılar VM 'Leri daha iyi anlamanıza yardımcı olur:

* [Azure Sanal Makineler’de SQL Server için yüksek kullanılabilirlik ve olağanüstü durum kurtarma](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-high-availability-dr)
* [Azure Sanal Makinelerde SQL Server için performansa yönelik en iyi yöntemler](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-performance)
* [Azure Sanal Makineler'de SQL Server için Uygulama Desenleri ve Geliştirme Stratejileri](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-app-patterns-dev-strategies)

Aşağıdaki bağlantılar, Azure SQL veritabanını daha iyi anlamanıza yardımcı olacaktır:

* [Azure SQL veritabanı sunucuları ve veritabanları oluşturma ve yönetme](https://docs.microsoft.com/azure/sql-database/sql-database-servers-databases)
* [Veritabanı Işlem birimleri (DTU 'Lar) ve elastik veritabanı Işlem birimleri (eDTU)](https://docs.microsoft.com/azure/sql-database/sql-database-what-is-a-dtu)
* [Azure SQL veritabanı kaynak limitleri](https://docs.microsoft.com/azure/sql-database/sql-database-resource-limits)

## <a name="choosing-iaas-or-paas"></a>IaaS veya PaaS seçme

Veritabanınızın nereye geçirilmesi gerektiğini değerlendirirken, IaaS veya PaaS 'nin sizin için uygun olup olmadığını saptayın.

**Şu durumlarda Azure VM 'lerinde SQL Server seçin:**

* Veritabanınızın ve uygulamalarınızın değişiklik yapmadan en az düzeyde "yükseltme ve kaydırma" yapmanız gerektiğini düşünüyorsunuz.
* Veritabanı sunucunuz ve üzerinde çalıştığı VM üzerinde tam denetim sahibi olmayı tercih edersiniz.
* Kullanmayı planladığınız SQL Server ve Windows Server lisanslarınız zaten var.

**Azure SQL Veritabanı'i aşağıdaki koşullar geçerli olduğunda tercih edin:**

* Uygulamalarınızı modernleştirin ve Azure 'daki diğer PaaS hizmetlerini kullanmak için geçiriyorsanız.
* Veritabanı sunucunuzu ve üzerinde çalıştığı VM 'yi yönetmek istemediğiniz.
* SQL Server veya Windows Server lisanslarınız yok ya da size zaman ermiş olan lisanslara izin vermek istiyordunuz.

Aşağıdaki tabloda, bir dizi senaryoya göre her bir hizmet arasındaki farklılıklar açıklanmaktadır.

| Senaryo | Azure VM 'lerinde SQL Server | Azure SQL Veritabanı |
|----------|-------------------------|--------------------|
| Geçiş | Veritabanınızda minimum değişiklik yapılmasını gerektirir. | [Data Migration Yardımcısı](https://www.microsoft.com/download/details.aspx?id=53595)tarafından belirlendiği şekilde, Azure SQL 'de kullanılamayan özellikler kullanıyorsanız veya yerel olarak yüklenen yürütülebilir dosyalar gibi başka bağımlılıklara sahipseniz veritabanınızda değişiklik yapılmasını gerektirebilir.|
| Kullanılabilirliği, kurtarmayı ve yükseltmeleri yönetme | Kullanılabilirlik ve kurtarma el ile yapılandırılır. Yükseltmeler, [VM Ölçek kümeleriyle](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade)otomatikleştirilebilir. | Sizin için otomatik olarak yönetilir. |
| Temel alınan işletim sistemi yapılandırması | El ile yapılandırma. | Sizin için otomatik olarak yönetilir. |
| Veritabanı boyutunu yönetme | SQL Server örneği başına 64 TB 'a kadar depolamayı destekler. | Yatay bölüme gerek duymadan önce 4 TB depolama alanı destekler. |
| Maliyetleri yönetme | SQL Server lisans maliyetlerini, Windows Server lisans maliyetlerini ve VM maliyetlerini (çekirdek, RAM ve depolamaya göre) yönetmeniz gerekir. | Hizmet maliyetlerini (bir elastik havuz kullanılıyorsa [eDTU 'ları veya DTU](https://docs.microsoft.com/azure/sql-database/sql-database-what-is-a-dtu)'ları, depolamayı ve veritabanlarının sayısını temel alarak) yönetmeniz gerekir. Ayrıca, herhangi bir SLA 'nın maliyetini yönetmeniz gerekir. |

İkisi arasındaki farklar hakkında daha fazla bilgi edinmek için, bir bulut seçin SQL Server seçeneğini belirleyin: Azure [SQL veritabanı veya Azure VM 'lerinde SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas).

## <a name="faq"></a>SSS

* **Azure VM 'lerinde veya Azure SQL veritabanı 'nda SQL Server SQL Server Management Studio ve SQL Server Reporting Services (SSRS) gibi araçları kullanmaya devam edebilir miyim?**

    Evet! Tüm Microsoft SQL araçları her iki hizmet ile de çalışmaktadır. SSRS, Azure SQL veritabanı 'nın bir parçası değildir, ancak bunu bir Azure VM 'de çalıştırmanız ve sonra bunu veritabanı örneğinize göstermelidir.

* **PaaS 'ye gitmek istiyorum, ancak Veritabanımın uyumlu olduğundan emin değildim. Yardım almak için araçlar var mı?**

    Evet. [Data Migration Yardımcısı](https://www.microsoft.com/download/details.aspx?id=53595) , Azure SQL veritabanı 'na geçiş bir parçası olarak kullanılan bir araçtır. [Azure veritabanı geçiş hizmeti](https://azure.microsoft.com/campaigns/database-migration/) , IaaS veya PaaS için kullanabileceğiniz bir önizleme hizmetidir.

* **Maliyetleri tahmin edebilir miyim?**

    Evet. [Azure Fiyatlandırma Hesaplayıcı](https://azure.microsoft.com/pricing/calculator/) , VM 'ler ve veritabanı hizmetleri dahil olmak üzere tüm Azure hizmetlerinin maliyetlerini tahmin etmek için kullanılabilir.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Doğru Azure barındırma seçeneğini belirleyin](choose.md)
