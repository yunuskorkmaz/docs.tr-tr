---
title: Entity FrameworkTypes için SqlClient
ms.date: 03/30/2017
ms.assetid: f2a95ead-c845-4e97-9fb3-04b444f7ed81
ms.openlocfilehash: af3a4eea08dd3f4e1a134fcb66d92bc4a3b077c7
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248375"
---
# <a name="sqlclient-for-entity-frameworktypes"></a>Entity FrameworkTypes için SqlClient
SQL Server (SqlClient) sağlayıcısı bildirim dosyası için .NET Framework Veri Sağlayıcısı, sağlayıcı temel türlerinin listesini, her tür için modelleri, kavramsal ve depolama modeli temel türleri arasındaki eşlemeleri ve yükseltme ve dönüştürme bilgilerini içerir kavramsal ve depolama modeli temel türleri arasındaki kurallar.  
  
 Aşağıdaki tabloda SQL Server 2008, SQL Server 2005 ve SQL Server 2000 veritabanları ve bu türlerin kavramsal model türleriyle nasıl eşlenme türleri açıklanmaktadır. SQL Server sonraki sürümlerinde bazı yeni türler sunulmuştur SQL Server eski sürümlerinde desteklenmez. Bu türler aşağıdaki tabloda belirtilmiştir.  
  
|Sağlayıcı türü<br /><br /> name|Sağlayıcı türü<br /><br /> öznitelikler|`EDMSimpleType`<br /><br /> name|Özellikleri|  
|----------------------------|----------------------------------|------------------------------|------------|  
|`bit`|yok|`Edm.Boolean`|yok|  
|`tinyint`|yok|`Edm.Byte`|yok|  
|`smallint`|yok|`Edm.Int16`|yok|  
|`int`|yok|`Edm.Int32`|yok|  
|`bigint`|yok|`Edm.Int64`|yok|  
|`float`|yok|`Edm.Double`|yok|  
|`real`|yok|`Edm.Double`|yok|  
|`decimal`|yok|`Edm.Decimal`|Duyarlılık<br /><br /> En düşük 1.<br /><br /> Çok 38<br /><br /> Varsayılanını 18<br /><br /> Sabit False<br /><br /> Ölçek<br /><br /> En düşük 0<br /><br /> Çok 38<br /><br /> Varsayılanını 0<br /><br /> Sabit False|  
|`numeric`|yok|`Edm.Decimal`|Duyarlılık<br /><br /> En düşük 1.<br /><br /> Çok 38<br /><br /> Varsayılanını 18<br /><br /> Sabit False<br /><br /> Ölçek<br /><br /> En düşük 0<br /><br /> Çok 38<br /><br /> Varsayılanını 0<br /><br /> Sabit False|  
|`smallmoney`|yok|`Edm.Decimal`|Duyarlılık<br /><br /> Varsayılanını 10<br /><br /> Sabit Doğru<br /><br /> Ölçek<br /><br /> Varsayılanını 4<br /><br /> Sabit Doğru|  
|`money`|yok|`Edm.Decimal`|Duyarlılık<br /><br /> Varsayılanını 19<br /><br /> Sabit Doğru<br /><br /> Ölçek<br /><br /> Varsayılanını 4<br /><br /> Sabit Doğru|  
|`binary`|yok|`Edm.Binary`|'In<br /><br /> En düşük 1.<br /><br /> Çok 8000<br /><br /> Varsayılanını 8000<br /><br /> Sabit False<br /><br /> FixedLength:<br /><br /> Varsayılanını Doğru<br /><br /> Sabit Doğru|  
|`varbinary`|yok|`Edm.Binary`|'In<br /><br /> En düşük 1.<br /><br /> Çok 8000<br /><br /> Varsayılanını 8000<br /><br /> Sabit False<br /><br /> FixedLength:<br /><br /> Varsayılanını False<br /><br /> Sabit Doğru|  
|`varbinary(max)`<br /><br /> Not: Bu tür SQL Server 2000 ' de desteklenmez.|yok|`Edm.Binary`|'In<br /><br /> Varsayılanını 214748364780<br /><br /> Sabit Doğru<br /><br /> FixedLength:<br /><br /> Varsayılanını False<br /><br /> Sabit Doğru|  
|`image`|yok|`Edm.Binary`|'In<br /><br /> Varsayılanını 2147483647<br /><br /> Sabit Doğru<br /><br /> FixedLength:<br /><br /> Varsayılanını False<br /><br /> Sabit Doğru|  
|`timestamp`|yok|`Edm.Binary`|'In<br /><br /> Varsayılanını 8<br /><br /> Sabit Doğru<br /><br /> FixedLength:<br /><br /> Varsayılanını Doğru<br /><br /> Sabit Doğru|  
|`rowversion`|yok|`Edm.Binary`|'In<br /><br /> Varsayılanını 8<br /><br /> Sabit Doğru<br /><br /> FixedLength:<br /><br /> Varsayılanını Doğru<br /><br /> Sabit Doğru|  
|`smalldatetime`|yok|`Edm.DateTime`|Duyarlılık<br /><br /> Varsayılanını 0<br /><br /> Sabit Doğru|  
|`datetime`|yok|`Edm.DateTime`|Duyarlılık<br /><br /> Varsayılanını 3<br /><br /> Sabit Doğru|  
|`date`<br /><br /> Not: Bu tür SQL Server 2005 ve SQL Server 2000 ' de desteklenmez.|yok|`Edm.DateTime`|Duyarlılık<br /><br /> Varsayılanını 0<br /><br /> Sabit False|  
|`time`<br /><br /> Not: Bu tür SQL Server 2005 ve SQL Server 2000 ' de desteklenmez.|yok|`Edm.Time`|Duyarlılık<br /><br /> Varsayılanını 7<br /><br /> Sabit False|  
|`datetime2`<br /><br /> Not: Bu tür SQL Server 2005 ve SQL Server 2000 ' de desteklenmez.|yok|`Edm.DateTime`|Duyarlılık<br /><br /> Varsayılanını 7<br /><br /> Sabit False|  
|`datetimeoffset`<br /><br /> Not: Bu tür SQL Server 2005 ve SQL Server 2000 ' de desteklenmez.|yok|`Edm.DateTimeOffset`|Duyarlılık<br /><br /> Varsayılanını 7<br /><br /> Sabit False|  
|`nvarchar`<br /><br /> Not: Bu tür SQL Server 2000 ' de desteklenmez.|yok|`Edm.String`|'In<br /><br /> En düşük 1.<br /><br /> Çok 4000<br /><br /> Varsayılanını 4000<br /><br /> Sabit False<br /><br /> Unicode:<br /><br /> Varsayılanını Doğru<br /><br /> Sabit Doğru<br /><br /> FixedLength:<br /><br /> Varsayılanını False<br /><br /> Sabit Doğru|  
|`varchar`<br /><br /> Not: Bu tür SQL Server 2000 ' de desteklenmez.|yok|`Edm.String`|'In<br /><br /> En düşük 1.<br /><br /> Çok 8000<br /><br /> Varsayılanını 8000<br /><br /> Sabit False<br /><br /> Unicode:<br /><br /> Varsayılanını False<br /><br /> Sabit Doğru<br /><br /> FixedLength:<br /><br /> Varsayılanını False<br /><br /> Sabit Doğru|  
|`char`|yok|`Edm.String`|'In<br /><br /> En düşük 1.<br /><br /> Çok 8000<br /><br /> Varsayılanını 8000<br /><br /> Sabit False<br /><br /> Unicode:<br /><br /> Varsayılanını False<br /><br /> Sabit Doğru<br /><br /> FixedLength:<br /><br /> Varsayılanını Doğru<br /><br /> Sabit Doğru|  
|`nchar`|yok|`Edm.String`|'In<br /><br /> En düşük 1.<br /><br /> Çok 4000<br /><br /> Varsayılanını 4000<br /><br /> Sabit False<br /><br /> Unicode:<br /><br /> Varsayılanını Doğru<br /><br /> Sabit Doğru<br /><br /> FixedLength:<br /><br /> Varsayılanını Doğru<br /><br /> Sabit Doğru|  
|`varchar`(`max`)|yok|`Edm.String`|'In<br /><br /> Varsayılanını 2147483647<br /><br /> Sabit Doğru<br /><br /> Unicode:<br /><br /> Varsayılanını False<br /><br /> Sabit Doğru<br /><br /> FixedLength:<br /><br /> Varsayılanını False<br /><br /> Sabit Doğru|  
|`nvarchar`(`max`)|yok|`Edm.String`|'In<br /><br /> Varsayılanını 1073741823<br /><br /> Sabit Doğru<br /><br /> Unicode:<br /><br /> Varsayılanını Doğru<br /><br /> Sabit Doğru<br /><br /> FixedLength:<br /><br /> Varsayılanını False<br /><br /> Sabit Doğru|  
|`ntext`|Eşit karşılaştırılabilir: False<br /><br /> Order karşılaştırılabilir: False|`Edm.String`|'In<br /><br /> Varsayılanını 1073741823<br /><br /> Sabit Doğru<br /><br /> Unicode:<br /><br /> Varsayılanını False<br /><br /> Sabit Doğru<br /><br /> FixedLength:<br /><br /> Varsayılanını False<br /><br /> Sabit Doğru|  
|`text`|Eşit karşılaştırılabilir: False<br /><br /> Order karşılaştırılabilir: False|`Edm.String`|'In<br /><br /> Varsayılanını 2147483647<br /><br /> Sabit Doğru<br /><br /> Unicode:<br /><br /> Varsayılanını False<br /><br /> Sabit Doğru<br /><br /> FixedLength:<br /><br /> Varsayılanını False<br /><br /> Sabit Doğru|  
|`Unique`<br /><br /> `identifier`|Eşit karşılaştırılabilir: Doğru<br /><br /> Order karşılaştırılabilir: Doğru|`Edm.Guid`|yok|  
|`xml`|Eşit karşılaştırılabilir: False<br /><br /> Order karşılaştırılabilir: False|`Edm.String`|'In<br /><br /> Varsayılanını 1073741823<br /><br /> Sabit Doğru<br /><br /> Unicode:<br /><br /> Varsayılanını Doğru<br /><br /> Sabit Doğru<br /><br /> FixedLength:<br /><br /> Varsayılanını False<br /><br /> Sabit Doğru|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CSDL, SSDL ve MSL Belirtimleri](./language-reference/csdl-ssdl-and-msl-specifications.md)
