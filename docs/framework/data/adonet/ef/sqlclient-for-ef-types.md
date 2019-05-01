---
title: Entity FrameworkTypes için SqlClient
ms.date: 03/30/2017
ms.assetid: f2a95ead-c845-4e97-9fb3-04b444f7ed81
ms.openlocfilehash: eb12bde1e319fde5adf20ad6cd54f8776aeda31d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879170"
---
# <a name="sqlclient-for-entity-frameworktypes"></a>Entity FrameworkTypes için SqlClient
SQL Server (SqlClient) sağlayıcısı bildirim dosyası için .NET Framework veri sağlayıcısı sağlayıcısı ilkel türler, her bir türü için modelleri kavramsal ve depolama modeli ilkel türlerini ve yükseltme ve dönüştürme arasındaki eşlemeleri listesini içerir. Kural kavramsal ve depolama modeli ilkel türler arasında.  
  
 Aşağıdaki tabloda, SQL Server 2008 için türleri açıklanmaktadır [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)], ve [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)] veritabanları ve nasıl eşleştiği bu tür için kavramsal model türleri. Bazı yeni türlerini sunulan SQL Server'ın sonraki sürümlerinde, SQL Server'ın eski sürümlerinde desteklenmez. Bu tür, aşağıdaki tabloda belirtilmiştir.  
  
|Sağlayıcı türü<br /><br /> name|Sağlayıcı türü<br /><br /> öznitelikler|`EDMSimpleType`<br /><br /> name|Özellikleri|  
|----------------------------|----------------------------------|------------------------------|------------|  
|`bit`|yok|`Edm.Boolean`|yok|  
|`tinyint`|yok|`Edm.Byte`|yok|  
|`smallint`|yok|`Edm.Int16`|yok|  
|`int`|yok|`Edm.Int32`|yok|  
|`bigint`|yok|`Edm.Int64`|yok|  
|`float`|yok|`Edm.Double`|yok|  
|`real`|yok|`Edm.Double`|yok|  
|`decimal`|yok|`Edm.Decimal`|Duyarlık:<br /><br /> -En az: 1.<br /><br /> -En fazla: 38<br /><br /> -Varsayılan: 18<br /><br /> -Sabit: False<br /><br /> Ölçek:<br /><br /> -En az: 0<br /><br /> -En fazla: 38<br /><br /> -Varsayılan: 0<br /><br /> -Sabit: False|  
|`numeric`|yok|`Edm.Decimal`|Duyarlık:<br /><br /> -En az: 1.<br /><br /> -En fazla: 38<br /><br /> -Varsayılan: 18<br /><br /> -Sabit: False<br /><br /> Ölçek:<br /><br /> -En az: 0<br /><br /> -En fazla: 38<br /><br /> -Varsayılan: 0<br /><br /> -Sabit: False|  
|`smallmoney`|yok|`Edm.Decimal`|Duyarlık:<br /><br /> -Varsayılan: 10<br /><br /> -Sabit: Doğru<br /><br /> Ölçek:<br /><br /> -Varsayılan: 4<br /><br /> -Sabit: Doğru|  
|`money`|yok|`Edm.Decimal`|Duyarlık:<br /><br /> -Varsayılan: 19<br /><br /> -Sabit: Doğru<br /><br /> Ölçek:<br /><br /> -Varsayılan: 4<br /><br /> -Sabit: Doğru|  
|`binary`|yok|`Edm.Binary`|MaxLength:<br /><br /> -En az: 1.<br /><br /> -En fazla: 8000<br /><br /> -Varsayılan: 8000<br /><br /> -Sabit: False<br /><br /> FixedLength:<br /><br /> -Varsayılan: Doğru<br /><br /> -Sabit: Doğru|  
|`varbinary`|yok|`Edm.Binary`|MaxLength:<br /><br /> -En az: 1.<br /><br /> -En fazla: 8000<br /><br /> -Varsayılan: 8000<br /><br /> -Sabit: False<br /><br /> FixedLength:<br /><br /> -Varsayılan: False<br /><br /> -Sabit: Doğru|  
|`varbinary(max)`<br /><br /> Not: Bu tür desteklenmiyor [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)].|yok|`Edm.Binary`|MaxLength:<br /><br /> -Varsayılan: 214748364780<br /><br /> -Sabit: Doğru<br /><br /> FixedLength:<br /><br /> -Varsayılan: False<br /><br /> -Sabit: Doğru|  
|`image`|yok|`Edm.Binary`|MaxLength:<br /><br /> -Varsayılan: 2147483647<br /><br /> -Sabit: Doğru<br /><br /> FixedLength:<br /><br /> -Varsayılan: False<br /><br /> -Sabit: Doğru|  
|`timestamp`|yok|`Edm.Binary`|MaxLength:<br /><br /> -Varsayılan: 8<br /><br /> -Sabit: Doğru<br /><br /> FixedLength:<br /><br /> -Varsayılan: Doğru<br /><br /> -Sabit: Doğru|  
|`rowversion`|yok|`Edm.Binary`|MaxLength:<br /><br /> -Varsayılan: 8<br /><br /> -Sabit: Doğru<br /><br /> FixedLength:<br /><br /> -Varsayılan: Doğru<br /><br /> -Sabit: Doğru|  
|`smalldatetime`|yok|`Edm.DateTime`|Duyarlık:<br /><br /> -Varsayılan: 0<br /><br /> -Sabit: Doğru|  
|`datetime`|yok|`Edm.DateTime`|Duyarlık:<br /><br /> -Varsayılan: 3<br /><br /> -Sabit: Doğru|  
|`date`<br /><br /> Not: Bu tür, SQL Server 2005 ve SQL Server 2000'de desteklenmiyor.|yok|`Edm.DateTime`|Duyarlık:<br /><br /> -Varsayılan: 0<br /><br /> -Sabit: False|  
|`time`<br /><br /> Not: Bu tür, SQL Server 2005 ve SQL Server 2000'de desteklenmiyor.|yok|`Edm.Time`|Duyarlık:<br /><br /> -Varsayılan: 7<br /><br /> -Sabit: False|  
|`datetime2`<br /><br /> Not: Bu tür, SQL Server 2005 ve SQL Server 2000'de desteklenmiyor.|yok|`Edm.DateTime`|Duyarlık:<br /><br /> -Varsayılan: 7<br /><br /> -Sabit: False|  
|`datetimeoffset`<br /><br /> Not: Bu tür, SQL Server 2005 ve SQL Server 2000'de desteklenmiyor.|yok|`Edm.DateTimeOffset`|Duyarlık:<br /><br /> -Varsayılan: 7<br /><br /> -Sabit: False|  
|`nvarchar`<br /><br /> Not: Bu tür desteklenmiyor [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)].|yok|`Edm.String`|MaxLength:<br /><br /> -En az: 1.<br /><br /> -En fazla: 4000<br /><br /> -Varsayılan: 4000<br /><br /> -Sabit: False<br /><br /> Unicode:<br /><br /> -Varsayılan: Doğru<br /><br /> -Sabit: Doğru<br /><br /> FixedLength:<br /><br /> -Varsayılan: False<br /><br /> -Sabit: Doğru|  
|`varchar`<br /><br /> Not: Bu tür desteklenmiyor [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)].|yok|`Edm.String`|MaxLength:<br /><br /> -En az: 1.<br /><br /> -En fazla: 8000<br /><br /> -Varsayılan: 8000<br /><br /> -Sabit: False<br /><br /> Unicode:<br /><br /> -Varsayılan: False<br /><br /> -Sabit: Doğru<br /><br /> FixedLength:<br /><br /> -Varsayılan: False<br /><br /> -Sabit: Doğru|  
|`char`|yok|`Edm.String`|MaxLength:<br /><br /> -En az: 1.<br /><br /> -En fazla: 8000<br /><br /> -Varsayılan: 8000<br /><br /> -Sabit: False<br /><br /> Unicode:<br /><br /> -Varsayılan: False<br /><br /> -Sabit: Doğru<br /><br /> FixedLength:<br /><br /> -Varsayılan: Doğru<br /><br /> -Sabit: Doğru|  
|`nchar`|yok|`Edm.String`|MaxLength:<br /><br /> -En az: 1.<br /><br /> -En fazla: 4000<br /><br /> -Varsayılan: 4000<br /><br /> -Sabit: False<br /><br /> Unicode:<br /><br /> -Varsayılan: Doğru<br /><br /> -Sabit: Doğru<br /><br /> FixedLength:<br /><br /> -Varsayılan: Doğru<br /><br /> -Sabit: Doğru|  
|`varchar`(`max`)|yok|`Edm.String`|MaxLength:<br /><br /> -Varsayılan: 2147483647<br /><br /> -Sabit: Doğru<br /><br /> Unicode:<br /><br /> -Varsayılan: False<br /><br /> -Sabit: Doğru<br /><br /> FixedLength:<br /><br /> -Varsayılan: False<br /><br /> -Sabit: Doğru|  
|`nvarchar`(`max`)|yok|`Edm.String`|MaxLength:<br /><br /> -Varsayılan: 1073741823<br /><br /> -Sabit: Doğru<br /><br /> Unicode:<br /><br /> -Varsayılan: Doğru<br /><br /> -Sabit: Doğru<br /><br /> FixedLength:<br /><br /> -Varsayılan: False<br /><br /> -Sabit: Doğru|  
|`ntext`|Eşittir karşılaştırılabilir: False<br /><br /> Sipariş karşılaştırılabilir: False|`Edm.String`|MaxLength:<br /><br /> -Varsayılan: 1073741823<br /><br /> -Sabit: Doğru<br /><br /> Unicode:<br /><br /> -Varsayılan: False<br /><br /> -Sabit: Doğru<br /><br /> FixedLength:<br /><br /> -Varsayılan: False<br /><br /> -Sabit: Doğru|  
|`text`|Eşittir karşılaştırılabilir: False<br /><br /> Sipariş karşılaştırılabilir: False|`Edm.String`|MaxLength:<br /><br /> -Varsayılan: 2147483647<br /><br /> -Sabit: Doğru<br /><br /> Unicode:<br /><br /> -Varsayılan: False<br /><br /> -Sabit: Doğru<br /><br /> FixedLength:<br /><br /> -Varsayılan: False<br /><br /> -Sabit: Doğru|  
|`Unique`<br /><br /> `identifier`|Eşittir karşılaştırılabilir: Doğru<br /><br /> Sipariş karşılaştırılabilir: Doğru|`Edm.Guid`|yok|  
|`xml`|Eşittir karşılaştırılabilir: False<br /><br /> Sipariş karşılaştırılabilir: False|`Edm.String`|MaxLength:<br /><br /> -Varsayılan: 1073741823<br /><br /> -Sabit: Doğru<br /><br /> Unicode:<br /><br /> -Varsayılan: Doğru<br /><br /> -Sabit: Doğru<br /><br /> FixedLength:<br /><br /> -Varsayılan: False<br /><br /> -Sabit: Doğru|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CSDL, SSDL ve MSL Belirtimleri](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
