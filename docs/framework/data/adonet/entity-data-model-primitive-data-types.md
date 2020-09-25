---
title: 'Varlık Veri Modeli: Basit Veri Türleri'
ms.date: 03/30/2017
ms.assetid: 7635168e-0566-4fdd-8391-7941b0d9f787
ms.openlocfilehash: 4d52f50dec44c7d667dfedc10a2c9c25fcde8917
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194823"
---
# <a name="entity-data-model-primitive-data-types"></a>Varlık Veri Modeli: Basit Veri Türleri

Varlık Veri Modeli (EDM), kavramsal bir modeldeki [özellikleri](property.md) tanımlamak için kullanılan bir dizi soyut temel veri türünü (dize, Boolean, Int32, vb.) destekler. Bu ilkel veri türleri, SQL Server veritabanı veya ortak dil çalışma zamanı (CLR) gibi depolama veya barındırma ortamında desteklenen gerçek temel veri türleri için proxy 'lardır. EDM, temel veri türleri üzerinden işlemler veya dönüştürmelerin semantiğini tanımlamaz; Bu semantikler depolama veya barındırma ortamı tarafından tanımlanır. Genellikle, EDM içindeki temel veri türleri depolama veya barındırma ortamındaki ilgili temel veri türlerine eşlenir. Entity Framework, EDM 'nin ilkel türlerini SQL Server veri türlerine nasıl eşlediğini hakkında bilgi için bkz. [Entity FrameworkTypes Için SqlClient](./ef/sqlclient-for-ef-types.md).  
  
> [!NOTE]
> EDM, temel veri türleri koleksiyonlarını desteklemez.  
  
 EDM içindeki yapılandırılmış veri türleri hakkında daha fazla bilgi için bkz. [varlık türü](entity-type.md) ve [karmaşık tür](complex-type.md).  
  
## <a name="primitive-data-types-supported-in-the-entity-data-model"></a>Varlık Veri Modeli desteklenen temel veri türleri  

 Aşağıdaki tabloda, EDM tarafından desteklenen temel veri türleri listelenmiştir. Tablo, her ilkel veri türüne uygulanabilecek [modelleri](facet.md) de listeler.  
  
|İlkel veri türü|Açıklama|Uygulanabilir modeller|  
|-------------------------|-----------------|-----------------------|  
|İkili|İkili verileri içerir.|MaxLength, FixedLength, Nullable, varsayılan|  
|Boole|Veya değerini içerir `true` `false` .|Null yapılabilir, varsayılan|  
|Bayt|İşaretsiz 8 bit tamsayı değeri içerir.|Duyarlılık, null yapılabilir, varsayılan|  
|DateTime|Bir tarih ve saati temsil eder.|Duyarlılık, null yapılabilir, varsayılan|  
|DateTimeOffset|GMT cinsinden dakika cinsinden bir tarih ve saat içerir.|Duyarlılık, null yapılabilir, varsayılan|  
|Ondalık|Sabit duyarlığa ve ölçeğe sahip sayısal bir değer içerir.|Duyarlılık, null yapılabilir, varsayılan|  
|Çift|15 basamaklı duyarlık içeren bir kayan nokta numarası içerir.|Duyarlılık, null yapılabilir, varsayılan|  
|Float|Yedi basamaklı duyarlık içeren bir kayan nokta numarası içerir.|Duyarlılık, null yapılabilir, varsayılan|  
|Guid|16 baytlık benzersiz bir tanımlayıcı içerir.|Duyarlılık, null yapılabilir, varsayılan|  
|Int16|İşaretli 16 bit tamsayı değeri içerir.|Duyarlılık, null yapılabilir, varsayılan|  
|Int32|İmzalı 32 bitlik bir tamsayı değeri içerir.|Duyarlılık, null yapılabilir, varsayılan|  
|Int64|İmzalı 64 bitlik bir tamsayı değeri içerir.|Duyarlılık, null yapılabilir, varsayılan|  
|SByte|İşaretli 8 bit tamsayı değeri içerir.|Duyarlılık, null yapılabilir, varsayılan|  
|Dize|Karakter verisi içerir.|Unicode, FixedLength, MaxLength, harmanlama, duyarlık, Nullable, varsayılan|  
|Süre|Günün saatini içerir.|Duyarlılık, null yapılabilir, varsayılan|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](entity-data-model.md)
