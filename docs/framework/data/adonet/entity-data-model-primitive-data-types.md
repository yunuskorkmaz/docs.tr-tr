---
title: "Varlık veri modeli: Basit veri türleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7635168e-0566-4fdd-8391-7941b0d9f787
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e9bf1298a5e3fbac82a931abcfb0919238d81bfb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="entity-data-model-primitive-data-types"></a>Varlık veri modeli: Basit veri türleri
Varlık veri modeli (EDM) tanımlamak için kullanılan soyut temel veri türleri (örneğin, dize, Boolean, Int32 ve benzeri), bir kümesini destekler [özellikleri](../../../../docs/framework/data/adonet/property.md) kavramsal modelde. Proxy, depolama veya bir SQL Server veritabanı veya ortak dil çalışma zamanı (CLR) gibi barındırma ortamına desteklenen gerçek temel veri türleri için bu temel veri türleridir. EDM ilkel veri türleri üzerinde işlemler veya dönüşümleri semantiği tanımlamaz; Bu semantiği depolama veya barındırma ortamı tarafından tanımlanır. Genellikle, EDM ilkel veri türleri, depolama veya barındırma ortamı karşılık gelen temel veri türleriyle eşlenir. Entity Framework EDM ilkel türlerinde SQL Server veri türleri için nasıl eşlendiğini hakkında daha fazla bilgi için bkz: [varlık FrameworkTypes SqlClient](../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).  
  
> [!NOTE]
>  EDM ilkel veri türler koleksiyonlarının desteklemez.  
  
 EDM yapısal veri türleri hakkında daha fazla bilgi için bkz: [varlık türü](../../../../docs/framework/data/adonet/entity-type.md) ve [karmaşık tür](../../../../docs/framework/data/adonet/complex-type.md).  
  
## <a name="primitive-data-types-supported-in-the-entity-data-model"></a>Varlık veri modeli desteklenen temel veri türleri  
 Aşağıdaki tabloda EDM tarafından desteklenen temel veri türlerini listeler. Ayrıca tabloda [modelleri](../../../../docs/framework/data/adonet/facet.md) her temel veri türü için uygulanabilir.  
  
|Basit veri türü|Açıklama|Geçerli modelleri|  
|-------------------------|-----------------|-----------------------|  
|İkili|İkili veriler içerir.|MaxLength, FixedLength, boş değer atanabilir, varsayılan|  
|Boole değeri|Değeri içeren `true` veya `false`.|Boş değer atanabilir, varsayılan|  
|Bayt|İmzasız 8 bit tamsayı değeri içerir.|Duyarlık boş değer atanabilir, varsayılan|  
|DateTime|Bir tarih ve saat temsil eder.|Duyarlık boş değer atanabilir, varsayılan|  
|DateTimeOffset|Bir tarih ve saat GMT'den dakika cinsinden uzaklık olarak içerir.|Duyarlık boş değer atanabilir, varsayılan|  
|Ondalık|Sabit duyarlık ve ölçek sayısal bir değer içerir.|Duyarlık boş değer atanabilir, varsayılan|  
|Çift|Kayan nokta ile 15 basamak duyarlıklı numarası içerir.|Duyarlık boş değer atanabilir, varsayılan|  
|Kayan nokta|Kayan nokta ile yedi basamaklı duyarlık numarası içerir.|Duyarlık boş değer atanabilir, varsayılan|  
|Guid|16 bayt benzersiz bir tanımlayıcı içerir.|Duyarlık boş değer atanabilir, varsayılan|  
|Int16|İşaretli 16 bit tamsayı değeri içerir.|Duyarlık boş değer atanabilir, varsayılan|  
|Int32|İşaretli 32 bit tamsayı değeri içerir.|Duyarlık boş değer atanabilir, varsayılan|  
|Int64|İşaretli 64-bit tamsayı değeri içerir.|Duyarlık boş değer atanabilir, varsayılan|  
|SByte|İşaretli 8 bit tam sayı değeri içerir.|Duyarlık boş değer atanabilir, varsayılan|  
|Dize|Karakter veri içeriyor.|Varsayılan Unicode, FixedLength, MaxLength, harmanlama, kesinlik, boş değer atanabilir,|  
|Zaman|Günün saati içerir.|Duyarlık boş değer atanabilir, varsayılan|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık Veri Modeli Temel Kavramları](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Varlık Veri Modeli](../../../../docs/framework/data/adonet/entity-data-model.md)
