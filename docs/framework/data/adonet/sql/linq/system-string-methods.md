---
title: System.String Yöntemleri
ms.date: 03/30/2017
ms.assetid: ce307f14-87e6-4816-8694-8a4147f6b784
ms.openlocfilehash: 583c0d58562c1605f24b61489d481e19248ebed4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792497"
---
# <a name="systemstring-methods"></a>System.String Yöntemleri
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Aşağıdaki <xref:System.String> yöntemleri desteklemez.  
  
## <a name="unsupported-systemstring-methods-in-general"></a>Genel olarak desteklenmeyen System. String yöntemleri  
 Genel <xref:System.String> olarak desteklenmeyen Yöntemler:  
  
- Kültüre duyarlı aşırı yüklemeler `CultureInfo`(bir  /  `StringComparison`  / alma yöntemi).`IFormatProvider`  
  
- `char` Dizi alan veya üreten Yöntemler.  
  
## <a name="unsupported-systemstring-static-methods"></a>Desteklenmeyen System. String statik yöntemleri  
  
|Desteklenmeyen System. String statik yöntemleri|  
|----------------------------------------------|  
|<xref:System.String.Copy%28System.String%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.Boolean%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.CompareOrdinal%28System.String%2CSystem.String%29?displayProperty=nameWithType>|  
|<xref:System.String.CompareOrdinal%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|  
  
## <a name="unsupported-systemstring-non-static-methods"></a>Desteklenmeyen System. String statik olmayan Yöntemler  
  
|Desteklenmeyen System. String statik olmayan Yöntemler|  
|---------------------------------------------------|  
|<xref:System.String.IndexOfAny%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.Split%2A?displayProperty=nameWithType>|  
|<xref:System.String.ToCharArray?displayProperty=nameWithType>|  
|<xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimEnd%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimStart%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
  
## <a name="differences-from-net"></a>.NET farklılıkları  
  
- Sorgular, sunucuda geçerli olabilecek SQL Server harmanlamaları yapmaz ve bu nedenle varsayılan olarak kültüre duyarlı, büyük/küçük harfe duyarsız karşılaştırmalar sağlar. Bu davranış, .NET Framework varsayılan, büyük/küçük harfe duyarlı anlamlarından farklıdır.  
  
- 0 döndürdüğünde, `NULL` dize ya da bulunan konum 0 ' dır. `LastIndexOf`  
  
- Bu türler otomatik olarak veritabanında doldurma işlemi yaptığından, birleştirme işleminden veya sabit uzunluklu dizelerde (`CHAR`, `NCHAR`) başka işlemlerden beklenmedik sonuçlar döndürülebilir.  
  
- `Replace` `SqlExceptions` `TEXT` `NTEXT` , ,Vegibibirçokyöntem,veyasütunlarıveXMLiçingeçerlibirçeviriolmadığından,normalşekilde`ToLower`çevrilmişseoluşur. `ToUpper` Bu davranış, bu türler için kabul edilebilir olarak değerlendirilir. Ancak, tüm `VARCHAR`dize işlemleri `VARCHAR(max)`, `NVARCHAR`,, ve `NVARCHAR(max)`için ortak dil çalışma zamanı (CLR) semantiğine uymalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Türleri ve İşlevleri](data-types-and-functions.md)
