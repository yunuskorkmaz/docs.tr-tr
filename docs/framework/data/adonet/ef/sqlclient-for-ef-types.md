---
title: Entity FrameworkTypes için SqlClient
ms.date: 03/30/2017
ms.assetid: f2a95ead-c845-4e97-9fb3-04b444f7ed81
ms.openlocfilehash: bca2cc0e0d9f43c51c66080f3bd38c245ce94381
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156595"
---
# <a name="sqlclient-for-entity-frameworktypes"></a>Entity FrameworkTypes için SqlClient

SQL Server (SqlClient) sağlayıcısı bildirim dosyası için .NET Framework Veri Sağlayıcısı, sağlayıcı temel türlerinin listesini, her tür için modelleri, kavramsal ve depolama modeli temel türleri arasındaki eşlemeleri ve kavramsal ve depolama modeli temel türleri arasındaki yükseltme ve dönüştürme kurallarını içerir.  
  
 Aşağıdaki tabloda SQL Server 2008, SQL Server 2005 ve SQL Server 2000 veritabanları ve bu türlerin kavramsal model türleriyle nasıl eşlenme türleri açıklanmaktadır. SQL Server sonraki sürümlerinde bazı yeni türler sunulmuştur SQL Server eski sürümlerinde desteklenmez. Bu türler aşağıdaki tabloda belirtilmiştir.  
  
|Sağlayıcı türü<br /><br /> name|Sağlayıcı türü<br /><br /> öznitelikler|`EDMSimpleType`<br /><br /> name|Modeller|  
|----------------------------|----------------------------------|------------------------------|------------|  
|`bit`|yok|`Edm.Boolean`|yok|  
|`tinyint`|yok|`Edm.Byte`|yok|  
|`smallint`|yok|`Edm.Int16`|yok|  
|`int`|yok|`Edm.Int32`|yok|  
|`bigint`|yok|`Edm.Int64`|yok|  
|`float`|yok|`Edm.Double`|yok|  
|`real`|yok|`Edm.Double`|yok|  
|`decimal`|yok|`Edm.Decimal`|Duyarlılık<br /><br /> -En az: 1<br /><br /> -En fazla: 38<br /><br /> -Varsayılan: 18<br /><br /> -Sabit: yanlış<br /><br /> Ölçek<br /><br /> -En az: 0<br /><br /> -En fazla: 38<br /><br /> -Varsayılan: 0<br /><br /> -Sabit: yanlış|  
|`numeric`|yok|`Edm.Decimal`|Duyarlılık<br /><br /> -En az: 1<br /><br /> -En fazla: 38<br /><br /> -Varsayılan: 18<br /><br /> -Sabit: yanlış<br /><br /> Ölçek<br /><br /> -En az: 0<br /><br /> -En fazla: 38<br /><br /> -Varsayılan: 0<br /><br /> -Sabit: yanlış|  
|`smallmoney`|yok|`Edm.Decimal`|Duyarlılık<br /><br /> -Varsayılan: 10<br /><br /> -Sabit: doğru<br /><br /> Ölçek<br /><br /> -Varsayılan: 4<br /><br /> -Sabit: doğru|  
|`money`|yok|`Edm.Decimal`|Duyarlılık<br /><br /> -Varsayılan: 19<br /><br /> -Sabit: doğru<br /><br /> Ölçek<br /><br /> -Varsayılan: 4<br /><br /> -Sabit: doğru|  
|`binary`|yok|`Edm.Binary`|'In<br /><br /> -En az: 1<br /><br /> -En fazla: 8000<br /><br /> -Varsayılan: 8000<br /><br /> -Sabit: yanlış<br /><br /> FixedLength:<br /><br /> -Varsayılan: true<br /><br /> -Sabit: doğru|  
|`varbinary`|yok|`Edm.Binary`|'In<br /><br /> -En az: 1<br /><br /> -En fazla: 8000<br /><br /> -Varsayılan: 8000<br /><br /> -Sabit: yanlış<br /><br /> FixedLength:<br /><br /> -Varsayılan: false<br /><br /> -Sabit: doğru|  
|`varbinary(max)`<br /><br /> Not: Bu tür SQL Server 2000 ' de desteklenmez.|yok|`Edm.Binary`|'In<br /><br /> -Varsayılan: 214748364780<br /><br /> -Sabit: doğru<br /><br /> FixedLength:<br /><br /> -Varsayılan: false<br /><br /> -Sabit: doğru|  
|`image`|yok|`Edm.Binary`|'In<br /><br /> -Varsayılan: 2147483647<br /><br /> -Sabit: doğru<br /><br /> FixedLength:<br /><br /> -Varsayılan: false<br /><br /> -Sabit: doğru|  
|`timestamp`|yok|`Edm.Binary`|'In<br /><br /> -Varsayılan: 8<br /><br /> -Sabit: doğru<br /><br /> FixedLength:<br /><br /> -Varsayılan: true<br /><br /> -Sabit: doğru|  
|`rowversion`|yok|`Edm.Binary`|'In<br /><br /> -Varsayılan: 8<br /><br /> -Sabit: doğru<br /><br /> FixedLength:<br /><br /> -Varsayılan: true<br /><br /> -Sabit: doğru|  
|`smalldatetime`|yok|`Edm.DateTime`|Duyarlılık<br /><br /> -Varsayılan: 0<br /><br /> -Sabit: doğru|  
|`datetime`|yok|`Edm.DateTime`|Duyarlılık<br /><br /> -Varsayılan: 3<br /><br /> -Sabit: doğru|  
|`date`<br /><br /> Not: Bu tür SQL Server 2005 ve SQL Server 2000 ' de desteklenmez.|yok|`Edm.DateTime`|Duyarlılık<br /><br /> -Varsayılan: 0<br /><br /> -Sabit: yanlış|  
|`time`<br /><br /> Not: Bu tür SQL Server 2005 ve SQL Server 2000 ' de desteklenmez.|yok|`Edm.Time`|Duyarlılık<br /><br /> -Varsayılan: 7<br /><br /> -Sabit: yanlış|  
|`datetime2`<br /><br /> Not: Bu tür SQL Server 2005 ve SQL Server 2000 ' de desteklenmez.|yok|`Edm.DateTime`|Duyarlılık<br /><br /> -Varsayılan: 7<br /><br /> -Sabit: yanlış|  
|`datetimeoffset`<br /><br /> Not: Bu tür SQL Server 2005 ve SQL Server 2000 ' de desteklenmez.|yok|`Edm.DateTimeOffset`|Duyarlılık<br /><br /> -Varsayılan: 7<br /><br /> -Sabit: yanlış|  
|`nvarchar`<br /><br /> Not: Bu tür SQL Server 2000 ' de desteklenmez.|yok|`Edm.String`|'In<br /><br /> -En az: 1<br /><br /> -En fazla: 4000<br /><br /> -Varsayılan: 4000<br /><br /> -Sabit: yanlış<br /><br /> Unicode:<br /><br /> -Varsayılan: true<br /><br /> -Sabit: doğru<br /><br /> FixedLength:<br /><br /> -Varsayılan: false<br /><br /> -Sabit: doğru|  
|`varchar`<br /><br /> Not: Bu tür SQL Server 2000 ' de desteklenmez.|yok|`Edm.String`|'In<br /><br /> -En az: 1<br /><br /> -En fazla: 8000<br /><br /> -Varsayılan: 8000<br /><br /> -Sabit: yanlış<br /><br /> Unicode:<br /><br /> -Varsayılan: false<br /><br /> -Sabit: doğru<br /><br /> FixedLength:<br /><br /> -Varsayılan: false<br /><br /> -Sabit: doğru|  
|`char`|yok|`Edm.String`|'In<br /><br /> -En az: 1<br /><br /> -En fazla: 8000<br /><br /> -Varsayılan: 8000<br /><br /> -Sabit: yanlış<br /><br /> Unicode:<br /><br /> -Varsayılan: false<br /><br /> -Sabit: doğru<br /><br /> FixedLength:<br /><br /> -Varsayılan: true<br /><br /> -Sabit: doğru|  
|`nchar`|yok|`Edm.String`|'In<br /><br /> -En az: 1<br /><br /> -En fazla: 4000<br /><br /> -Varsayılan: 4000<br /><br /> -Sabit: yanlış<br /><br /> Unicode:<br /><br /> -Varsayılan: true<br /><br /> -Sabit: doğru<br /><br /> FixedLength:<br /><br /> -Varsayılan: true<br /><br /> -Sabit: doğru|  
|`varchar`(`max`)|yok|`Edm.String`|'In<br /><br /> -Varsayılan: 2147483647<br /><br /> -Sabit: doğru<br /><br /> Unicode:<br /><br /> -Varsayılan: false<br /><br /> -Sabit: doğru<br /><br /> FixedLength:<br /><br /> -Varsayılan: false<br /><br /> -Sabit: doğru|  
|`nvarchar`(`max`)|yok|`Edm.String`|'In<br /><br /> -Varsayılan: 1073741823<br /><br /> -Sabit: doğru<br /><br /> Unicode:<br /><br /> -Varsayılan: true<br /><br /> -Sabit: doğru<br /><br /> FixedLength:<br /><br /> -Varsayılan: false<br /><br /> -Sabit: doğru|  
|`ntext`|Eşit karşılaştırılabilir: false<br /><br /> Order karşılaştırılabilir: false|`Edm.String`|'In<br /><br /> -Varsayılan: 1073741823<br /><br /> -Sabit: doğru<br /><br /> Unicode:<br /><br /> -Varsayılan: false<br /><br /> -Sabit: doğru<br /><br /> FixedLength:<br /><br /> -Varsayılan: false<br /><br /> -Sabit: doğru|  
|`text`|Eşit karşılaştırılabilir: false<br /><br /> Order karşılaştırılabilir: false|`Edm.String`|'In<br /><br /> -Varsayılan: 2147483647<br /><br /> -Sabit: doğru<br /><br /> Unicode:<br /><br /> -Varsayılan: false<br /><br /> -Sabit: doğru<br /><br /> FixedLength:<br /><br /> -Varsayılan: false<br /><br /> -Sabit: doğru|  
|`Unique`<br /><br /> `identifier`|Eşit karşılaştırılabilir: doğru<br /><br /> Sipariş karşılaştırması: doğru|`Edm.Guid`|yok|  
|`xml`|Eşit karşılaştırılabilir: false<br /><br /> Order karşılaştırılabilir: false|`Edm.String`|'In<br /><br /> -Varsayılan: 1073741823<br /><br /> -Sabit: doğru<br /><br /> Unicode:<br /><br /> -Varsayılan: true<br /><br /> -Sabit: doğru<br /><br /> FixedLength:<br /><br /> -Varsayılan: false<br /><br /> -Sabit: doğru|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CSDL, SSDL ve MSL Belirtimleri](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
