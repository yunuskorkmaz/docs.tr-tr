---
title: Varlık FrameworkTypes SqlClient
ms.date: 03/30/2017
ms.assetid: f2a95ead-c845-4e97-9fb3-04b444f7ed81
ms.openlocfilehash: f5b471cea4f26c06e8af77298c256bff97ef21de
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766549"
---
# <a name="sqlclient-for-entity-frameworktypes"></a>Varlık FrameworkTypes SqlClient
SQL Server (SqlClient) sağlayıcı bildirim dosyası için .NET Framework veri sağlayıcısı sağlayıcısı ilkel türler, her bir türü için modelleri kavramsal ve depolama modeli ilkel türlerini ve yükseltme ve dönüştürme arasındaki eşlemeleri listesini içerir kavramsal ve depolama modeli ilkel türlerini arasındaki kuralları.  
  
 Aşağıdaki tabloda, SQL Server 2008 için türleri açıklanmaktadır [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)], ve [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)] veritabanları ve bu tür için kavramsal eşleme nasıl model türü. Bazı yeni türleri de tanıtılan SQL Server'ın sonraki sürümleri, SQL Server'ın daha eski sürümlerinde desteklenmez. Bu tür, aşağıdaki tabloda belirtilmiştir.  
  
|Sağlayıcı türü<br /><br /> name|Sağlayıcı türü<br /><br /> öznitelikler|`EDMSimpleType`<br /><br /> name|Özellikleri|  
|----------------------------|----------------------------------|------------------------------|------------|  
|`bit`|yok|`Edm.Boolean`|yok|  
|`tinyint`|yok|`Edm.Byte`|yok|  
|`smallint`|yok|`Edm.Int16`|yok|  
|`int`|yok|`Edm.Int32`|yok|  
|`bigint`|yok|`Edm.Int64`|yok|  
|`float`|yok|`Edm.Double`|yok|  
|`real`|yok|`Edm.Double`|yok|  
|`decimal`|yok|`Edm.Decimal`|Duyarlık:<br /><br /> -En az: 1<br /><br /> -En fazla: 38<br /><br /> -Varsayılan: 18<br /><br /> -Sabit: yanlış<br /><br /> Ölçek:<br /><br /> -En düşük: 0<br /><br /> -En fazla: 38<br /><br /> -Varsayılan: 0<br /><br /> -Sabit: yanlış|  
|`numeric`|yok|`Edm.Decimal`|Duyarlık:<br /><br /> -En az: 1<br /><br /> -En fazla: 38<br /><br /> -Varsayılan: 18<br /><br /> -Sabit: yanlış<br /><br /> Ölçek:<br /><br /> -En düşük: 0<br /><br /> -En fazla: 38<br /><br /> -Varsayılan: 0<br /><br /> -Sabit: yanlış|  
|`smallmoney`|yok|`Edm.Decimal`|Duyarlık:<br /><br /> -Varsayılan: 10<br /><br /> -Sabit: True<br /><br /> Ölçek:<br /><br /> -Varsayılan: 4<br /><br /> -Sabit: True|  
|`money`|yok|`Edm.Decimal`|Duyarlık:<br /><br /> -Varsayılan: 19<br /><br /> -Sabit: True<br /><br /> Ölçek:<br /><br /> -Varsayılan: 4<br /><br /> -Sabit: True|  
|`binary`|yok|`Edm.Binary`|MaxLength:<br /><br /> -En az: 1<br /><br /> -En fazla: 8000<br /><br /> -Varsayılan: 8000<br /><br /> -Sabit: yanlış<br /><br /> FixedLength:<br /><br /> -Varsayılan: True<br /><br /> -Sabit: True|  
|`varbinary`|yok|`Edm.Binary`|MaxLength:<br /><br /> -En az: 1<br /><br /> -En fazla: 8000<br /><br /> -Varsayılan: 8000<br /><br /> -Sabit: yanlış<br /><br /> FixedLength:<br /><br /> -Varsayılan: False<br /><br /> -Sabit: True|  
|`varbinary(max)`<br /><br /> Not: Bu tür desteklenmeyen [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)].|yok|`Edm.Binary`|MaxLength:<br /><br /> -Varsayılan: 214748364780<br /><br /> -Sabit: True<br /><br /> FixedLength:<br /><br /> -Varsayılan: False<br /><br /> -Sabit: True|  
|`image`|yok|`Edm.Binary`|MaxLength:<br /><br /> -Varsayılan: 2147483647<br /><br /> -Sabit: True<br /><br /> FixedLength:<br /><br /> -Varsayılan: False<br /><br /> -Sabit: True|  
|`timestamp`|yok|`Edm.Binary`|MaxLength:<br /><br /> -Varsayılan: 8<br /><br /> -Sabit: True<br /><br /> FixedLength:<br /><br /> -Varsayılan: True<br /><br /> -Sabit: True|  
|`rowversion`|yok|`Edm.Binary`|MaxLength:<br /><br /> -Varsayılan: 8<br /><br /> -Sabit: True<br /><br /> FixedLength:<br /><br /> -Varsayılan: True<br /><br /> -Sabit: True|  
|`smalldatetime`|yok|`Edm.DateTime`|Duyarlık:<br /><br /> -Varsayılan: 0<br /><br /> -Sabit: True|  
|`datetime`|yok|`Edm.DateTime`|Duyarlık:<br /><br /> -Varsayılan: 3<br /><br /> -Sabit: True|  
|`date`<br /><br /> Not: SQL Server 2005 ve SQL Server 2000'de bu türü desteklenmiyor.|yok|`Edm.DateTime`|Duyarlık:<br /><br /> -Varsayılan: 0<br /><br /> -Sabit: yanlış|  
|`time`<br /><br /> Not: SQL Server 2005 ve SQL Server 2000'de bu türü desteklenmiyor.|yok|`Edm.Time`|Duyarlık:<br /><br /> -Varsayılan: 7<br /><br /> -Sabit: yanlış|  
|`datetime2`<br /><br /> Not: SQL Server 2005 ve SQL Server 2000'de bu türü desteklenmiyor.|yok|`Edm.DateTime`|Duyarlık:<br /><br /> -Varsayılan: 7<br /><br /> -Sabit: yanlış|  
|`datetimeoffset`<br /><br /> Not: SQL Server 2005 ve SQL Server 2000'de bu türü desteklenmiyor.|yok|`Edm.DateTimeOffset`|Duyarlık:<br /><br /> -Varsayılan: 7<br /><br /> -Sabit: yanlış|  
|`nvarchar`<br /><br /> Not: Bu tür desteklenmeyen [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)].|yok|`Edm.String`|MaxLength:<br /><br /> -En az: 1<br /><br /> -En fazla: 4000<br /><br /> -Varsayılan: 4000<br /><br /> -Sabit: yanlış<br /><br /> Unicode:<br /><br /> -Varsayılan: True<br /><br /> -Sabit: True<br /><br /> FixedLength:<br /><br /> -Varsayılan: False<br /><br /> -Sabit: True|  
|`varchar`<br /><br /> Not: Bu tür desteklenmeyen [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)].|yok|`Edm.String`|MaxLength:<br /><br /> -En az: 1<br /><br /> -En fazla: 8000<br /><br /> -Varsayılan: 8000<br /><br /> -Sabit: yanlış<br /><br /> Unicode:<br /><br /> -Varsayılan: False<br /><br /> -Sabit: True<br /><br /> FixedLength:<br /><br /> -Varsayılan: False<br /><br /> -Sabit: True|  
|`char`|yok|`Edm.String`|MaxLength:<br /><br /> -En az: 1<br /><br /> -En fazla: 8000<br /><br /> -Varsayılan: 8000<br /><br /> -Sabit: yanlış<br /><br /> Unicode:<br /><br /> -Varsayılan: False<br /><br /> -Sabit: True<br /><br /> FixedLength:<br /><br /> -Varsayılan: True<br /><br /> -Sabit: True|  
|`nchar`|yok|`Edm.String`|MaxLength:<br /><br /> -En az: 1<br /><br /> -En fazla: 4000<br /><br /> -Varsayılan: 4000<br /><br /> -Sabit: yanlış<br /><br /> Unicode:<br /><br /> -Varsayılan: True<br /><br /> -Sabit: True<br /><br /> FixedLength:<br /><br /> -Varsayılan: True<br /><br /> -Sabit: True|  
|`varchar`(`max`)|yok|`Edm.String`|MaxLength:<br /><br /> -Varsayılan: 2147483647<br /><br /> -Sabit: True<br /><br /> Unicode:<br /><br /> -Varsayılan: False<br /><br /> -Sabit: True<br /><br /> FixedLength:<br /><br /> -Varsayılan: False<br /><br /> -Sabit: True|  
|`nvarchar`(`max`)|yok|`Edm.String`|MaxLength:<br /><br /> -Varsayılan: 1073741823<br /><br /> -Sabit: True<br /><br /> Unicode:<br /><br /> -Varsayılan: True<br /><br /> -Sabit: True<br /><br /> FixedLength:<br /><br /> -Varsayılan: False<br /><br /> -Sabit: True|  
|`ntext`|Eşitlik için karşılaştırılabilir: yanlış<br /><br /> Sıralı karşılaştırılabilir: yanlış|`Edm.String`|MaxLength:<br /><br /> -Varsayılan: 1073741823<br /><br /> -Sabit: True<br /><br /> Unicode:<br /><br /> -Varsayılan: False<br /><br /> -Sabit: True<br /><br /> FixedLength:<br /><br /> -Varsayılan: False<br /><br /> -Sabit: True|  
|`text`|Eşitlik için karşılaştırılabilir: yanlış<br /><br /> Sıralı karşılaştırılabilir: yanlış|`Edm.String`|MaxLength:<br /><br /> -Varsayılan: 2147483647<br /><br /> -Sabit: True<br /><br /> Unicode:<br /><br /> -Varsayılan: False<br /><br /> -Sabit: True<br /><br /> FixedLength:<br /><br /> -Varsayılan: False<br /><br /> -Sabit: True|  
|`Unique`<br /><br /> `identifier`|Eşitlik için karşılaştırılabilir: True<br /><br /> Sıralı karşılaştırılabilir: True|`Edm.Guid`|yok|  
|`xml`|Eşitlik için karşılaştırılabilir: yanlış<br /><br /> Sıralı karşılaştırılabilir: yanlış|`Edm.String`|MaxLength:<br /><br /> -Varsayılan: 1073741823<br /><br /> -Sabit: True<br /><br /> Unicode:<br /><br /> -Varsayılan: True<br /><br /> -Sabit: True<br /><br /> FixedLength:<br /><br /> -Varsayılan: False<br /><br /> -Sabit: True|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CSDL, SSDL ve MSL Belirtimleri](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
