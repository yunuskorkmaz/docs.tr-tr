---
title: System.String Yöntemleri
ms.date: 03/30/2017
ms.assetid: ce307f14-87e6-4816-8694-8a4147f6b784
ms.openlocfilehash: c988bf7f04b284b0d352cd9e495931543980fdba
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64613749"
---
# <a name="systemstring-methods"></a>System.String Yöntemleri
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] şunları desteklemez <xref:System.String> yöntemleri.  
  
## <a name="unsupported-systemstring-methods-in-general"></a>System.String yöntemleri genel desteklenmiyor  
 Desteklenmeyen <xref:System.String> genel yöntemler:  
  
- Kültüre duyarlı aşırı yüklemeler (ele yöntemleri bir `CultureInfo`  /  `StringComparison`  /  `IFormatProvider`).  
  
- Alabilir veya üretmek yöntemleri bir `char` dizi.  
  
## <a name="unsupported-systemstring-static-methods"></a>Desteklenmeyen System.String statik yöntemleri  
  
|Desteklenmeyen System.String statik yöntemleri|  
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
  
## <a name="unsupported-systemstring-non-static-methods"></a>Desteklenmeyen System.String statik olmayan metotlar  
  
|Desteklenmeyen System.String statik olmayan metotlar|  
|---------------------------------------------------|  
|<xref:System.String.IndexOfAny%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.Split%2A?displayProperty=nameWithType>|  
|<xref:System.String.ToCharArray?displayProperty=nameWithType>|  
|<xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimEnd%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimStart%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
  
## <a name="differences-from-net"></a>.NET arasındaki farklar  
  
- Sorgular, sunucu üzerinde etkin olabilir ve bu nedenle varsayılan olarak kültüre duyarlı ve büyük küçük harf duyarsız karşılaştırmalarını sağlar, SQL Server harmanlamaları için hesap kullanılamıyor. Bu davranış, varsayılan, .NET Framework'ün büyük/küçük harfe semantiği farklıdır.  
  
- Zaman `LastIndexOf` döndürür ya da dize 0 `NULL` veya bulunan konumu 0'dır.  
  
- Beklenmeyen sonuçlar birleştirme ya da sabit uzunluklu dizeler üzerinde başka işlemler döndürülmesi (`CHAR`, `NCHAR`), bu tür, veritabanında uygulanan doldurma otomatik olarak sahip olursunuz.  
  
- Çünkü birçok yöntem gibi `Replace`, `ToLower`, `ToUpper`ve geçerli çeviri için sahip karakter dizin oluşturucu `TEXT` veya `NTEXT` sütunları ve XML `SqlExceptions` normalde çevrilmiş ortaya. Bu davranışı Bu türleri için kabul edilebilir olarak kabul edilir. Ancak, tüm dize işlemleri için ortak dil çalışma zamanı (CLR) semantiği eşleşmelidir `VARCHAR`, `NVARCHAR`, `VARCHAR(max)`, ve `NVARCHAR(max)`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Türleri ve İşlevleri](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
