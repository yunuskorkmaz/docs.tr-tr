---
title: "System.String yöntemleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce307f14-87e6-4816-8694-8a4147f6b784
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 43e0a2904603019c3237a52402495997d1e140e6
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="systemstring-methods"></a>System.String yöntemleri
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Aşağıdaki desteklemiyor <xref:System.String> yöntemleri.  
  
## <a name="unsupported-systemstring-methods-in-general"></a>System.String yöntemleri genel desteklenmiyor  
 Desteklenmeyen <xref:System.String> genel yöntemleri:  
  
-   Kültüre duyarlı aşırı (ele yöntemleri bir `CultureInfo`  /  `StringComparison`  /  `IFormatProvider`).  
  
-   Alabilir veya üretmek yöntemleri bir `char` dizi.  
  
## <a name="unsupported-systemstring-static-methods"></a>Desteklenmeyen System.String statik yöntemler  
  
|Desteklenmeyen System.String statik yöntemler|  
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
  
## <a name="unsupported-systemstring-non-static-methods"></a>Desteklenmeyen System.String statik olmayan yöntemleri  
  
|Desteklenmeyen System.String statik olmayan yöntemleri|  
|---------------------------------------------------|  
|<xref:System.String.IndexOfAny%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.Split%2A?displayProperty=nameWithType>|  
|<xref:System.String.ToCharArray?displayProperty=nameWithType>|  
|<xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimEnd%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimStart%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
  
## <a name="differences-from-net"></a>.NET arasındaki farklar  
  
-   Sorguları sunucu üzerinde etkin olabilir ve bu nedenle varsayılan kültüre duyarlı, büyük küçük harf duyarsız karşılaştırma sağlar SQL Server harmanlamaları hesabı değil. Bu davranış varsayılan olarak .NET Framework'ün büyük küçük harfe duyarlı semantiği farklıdır.  
  
-   Zaman `LastIndexOf` döndürür 0, her iki dize `NULL` veya 0 bulunan konumdur.  
  
-   Beklenmeyen sonuçlara neden olabilir döndürülen birleştirme veya sabit uzunluklu dizeler üzerinde başka işlemler (`CHAR`, `NCHAR`), bu türlerinin veritabanında uygulanan doldurma otomatik olarak vardır.  
  
-   İçin birçok yöntem gibi `Replace`, `ToLower`, `ToUpper`ve hiçbir geçerli çeviri sahip karakter dizin oluşturucu `TEXT` veya `NTEXT` sütunlar ve XML `SqlExceptions` normalde çevrilen ortaya. Bu davranış bu türleri için kabul edilebilir olarak kabul edilir. Ancak, tüm dize işlemleri için ortak dil çalışma zamanı (CLR) semantiği eşleşmelidir `VARCHAR`, `NVARCHAR`, `VARCHAR(max)`, ve `NVARCHAR(max)`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Türleri ve İşlevleri](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
