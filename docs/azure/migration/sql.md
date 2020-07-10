---
title: Azure’a SQL Server veritabanını geçirme
description: SQL Server veritabanını şirket içi SQL Server Azure 'a geçirmeyi öğrenin.
ms.topic: how-to
ms.date: 05/27/2020
ms.openlocfilehash: 5f191cafbff3823d04e1dbd1fdf81e1157e20999
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174289"
---
# <a name="migrate-a-sql-server-database-to-azure"></a>Azure’a SQL Server veritabanını geçirme

Bu makalede, SQL Server veritabanını Azure 'a geçirmek için iki seçenekten oluşan kısa bir ana hat sunulmaktadır. Azure 'da bir üretim SQL Server veritabanının geçirilmesi için üç birincil seçenek bulunur. Bu makale aşağıdaki iki seçeneğe odaklanmaktadır:

1. [Azure VM 'lerinde SQL Server](/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-iaas-overview): Azure 'da çalışan ve hizmet olarak altyapı (IaaS) olarak da bilinen bir Windows sanal makinesinde yüklü ve barındırılan bir SQL Server örneği.
2. [Azure SQL veritabanı](/azure/sql-database/sql-database-technical-overview): hizmet olarak platform (PaaS) olarak da bilinen, tam olarak YÖNETILEN bir SQL veritabanı Azure hizmetidir.

Her ikisi de, geçirmeden önce değerlendirmeniz gereken profesyonelleri ve dezavantajlarla birlikte gelir. Üçüncü seçenek [Azure SQL veritabanı yönetilen örnekleri](/azure/sql-database/sql-database-managed-instance)olur.

## <a name="get-started"></a>başlarken

Kullandığınız hizmete bağlı olarak aşağıdaki geçiş kılavuzlarınız yararlı olacaktır:

* [Bir SQL Server veritabanını Azure VM’deki SQL Server’a geçirme](/azure/virtual-machines/windows/sql/virtual-machines-windows-migrate-sql)
* [SQL Server veritabanınızı Azure SQL Veritabanına geçirme](/azure/sql-database/sql-database-migrate-your-sql-server-database)

Ayrıca, kavramsal içeriğe yönelik aşağıdaki bağlantılar VM 'Leri daha iyi anlamanıza yardımcı olur:

* [Azure Sanal Makineler’de SQL Server için yüksek kullanılabilirlik ve olağanüstü durum kurtarma](/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-high-availability-dr)
* [Azure Sanal Makinelerde SQL Server için performansa yönelik en iyi yöntemler](/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-performance)
* [Azure Sanal Makineler'de SQL Server için Uygulama Desenleri ve Geliştirme Stratejileri](/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-app-patterns-dev-strategies)

Aşağıdaki bağlantılar, Azure SQL veritabanını daha iyi anlamanıza yardımcı olacaktır:

* [Azure SQL veritabanı sunucuları ve veritabanları oluşturma ve yönetme](/azure/sql-database/sql-database-servers-databases)
* [Veritabanı Işlem birimleri (DTU 'Lar) ve elastik veritabanı Işlem birimleri (eDTU)](/azure/sql-database/sql-database-what-is-a-dtu)
* [Azure SQL veritabanı kaynak limitleri](/azure/sql-database/sql-database-resource-limits)

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
| Kullanılabilirliği, kurtarmayı ve yükseltmeleri yönetme | Kullanılabilirlik ve kurtarma el ile yapılandırılır. Yükseltmeler, [VM Ölçek kümeleriyle](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade)otomatikleştirilebilir. | Sizin için otomatik olarak yönetilir. |
| Temel alınan işletim sistemi yapılandırması | El ile yapılandırma. | Sizin için otomatik olarak yönetilir. |
| Veritabanı boyutunu yönetme | SQL Server örneği başına 256 TB 'a kadar depolamayı destekler. | Yatay bölüme gerek duymadan önce 8 TB depolamayı destekler. |
| Maliyetleri yönetme | SQL Server lisans maliyetlerini, Windows Server lisans maliyetlerini ve VM maliyetlerini (çekirdek, RAM ve depolamaya göre) yönetmeniz gerekir. | Hizmet maliyetlerini (bir elastik havuz kullanılıyorsa [eDTU 'ları veya DTU](/azure/sql-database/sql-database-what-is-a-dtu)'ları, depolamayı ve veritabanlarının sayısını temel alarak) yönetmeniz gerekir. Ayrıca, herhangi bir SLA 'nın maliyetini yönetmeniz gerekir. |

İkisi arasındaki farklar hakkında daha fazla bilgi edinmek için bkz. [Azure SQL 'de doğru dağıtım seçeneğini seçme](/azure/sql-database/sql-database-paas-vs-sql-server-iaas).

## <a name="faq"></a>SSS

* **Azure VM 'lerinde veya Azure SQL veritabanı 'nda SQL Server SQL Server Management Studio ve SQL Server Reporting Services (SSRS) gibi araçları kullanmaya devam edebilir miyim?**

    Evet. Tüm Microsoft SQL araçları her iki hizmet ile de çalışmaktadır. SSRS, Azure SQL veritabanı 'nın bir parçası değildir, ancak bunu bir Azure VM 'de çalıştırmanız ve sonra bunu veritabanı örneğinize göstermelidir.

* **PaaS 'ye gitmek istiyorum, ancak Veritabanımın uyumlu olduğundan emin değildim. Yardım almak için araçlar var mı?**

    Evet. [Data Migration Yardımcısı](https://www.microsoft.com/download/details.aspx?id=53595) , Azure SQL veritabanı 'na geçiş bir parçası olarak kullanılan bir araçtır. [Azure veritabanı geçiş hizmeti](https://azure.microsoft.com/campaigns/database-migration/) , IaaS veya PaaS için kullanabileceğiniz bir önizleme hizmetidir.

* **Maliyetleri tahmin edebilir miyim?**

    Evet. [Azure Fiyatlandırma Hesaplayıcı](https://azure.microsoft.com/pricing/calculator/) , VM 'ler ve veritabanı hizmetleri dahil olmak üzere tüm Azure hizmetlerinin maliyetlerini tahmin etmek için kullanılabilir.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Doğru Azure barındırma seçeneğini belirleyin](choose.md)
