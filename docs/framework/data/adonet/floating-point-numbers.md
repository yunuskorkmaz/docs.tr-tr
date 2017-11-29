---
title: "Kayan nokta sayıları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 73c218c6-1c44-4402-a167-4f6262629a91
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c3e8ac8b5a97c62bb173fba57ac8aeb26a1dad42
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="floating-point-numbers"></a>Kayan nokta sayıları
Bu konuda kayan nokta sayıları ile çalışırken, geliştiricilerin sık karşılaşırsanız sorunlardan bazıları açıklanmaktadır [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]. Bu sorunları şekilde bilgisayarlar kayan nokta sayıları depolamak ve gibi belirli bir sağlayıcıya özgü olmayan neden olduğu <xref:System.Data.SqlClient> veya <xref:System.Data.OracleClient>.  
  
 Kayan nokta sayıları genellikle tam bir ikili temsili sahip değilsiniz. Bunun yerine, bilgisayar yaklaşık numarasını depolar. Farklı zamanlarda farklı sayıda ikili basamak sayısı temsil etmek için kullanılabilir. Kayan zaman noktası numarası bir gösteriminden başka bir gösterimi, bu sayının en az önemli basamak dönüştürülür biraz farklılık gösterebilir. Dönüştürme, genellikle numarası başka bir türüne bir türden diğerine dönüştürün oluşur. Değişim dönüştürme türleri veya veritabanı değerlerini temsil eden türler arasında bir veritabanı içinde oluşup oluşmadığını oluşur. Bu değişiklikler nedeniyle, bunları farklı değerlere sahip neden bunların en az önemli basamak değişiklikleri mantıksal olarak eşit olacak numaraları sahip olabilir. Duyarlık numarasındaki basamak sayısı daha büyük ya da beklenenden daha küçük olabilir. Dize olarak biçimlendirilmiş zaman sayısı beklenen değerle göstermeyebilir.  
  
 Bu etkilerle en aza indirmek için kullanabileceğiniz sayısal türler arasında en yakın eşleşme kullanmanız gerekir. Örneğin, birlikte çalıştığınız [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)], gerçek tür Transact-SQL değeri float türü değeri dönüştürürseniz, tam bir sayısal değer değişebilir. İçinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], dönüştürme bir <xref:System.Single> için bir <xref:System.Double> da beklenmeyen sonuçlara neden olabilir. Her iki durumda, iyi bir stratejisi uygulama kullanımı aynı sayısal tür tüm değerleri olmasını sağlamaktır. Bir sabit duyarlıklı ondalık türü kullanın veya bunlarla çalışmadan önce kayan nokta sayıları bir sabit duyarlıklı ondalık türüne dönüştürün.  
  
 Eşitlik karşılaştırması sorunları gidermek için en az önemli basamak Çeşitlemeler göz ardı edilir böylece uygulamanız kodlama göz önünde bulundurun. Örneğin, iki sayıyı eşit olup olmadığını görmek için karşılaştırma yerine başka bir sayıyı arasında bir sayı çıkarın. Fark Yuvarlamanın kabul edilebilir bir kenar boşluğu içinde ise, aynı şekilde iseler, uygulamanızın sayıları davranabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kayan noktalı sayıların neden duyarlık kaybedebileceği](http://msdn.microsoft.com/library/1acb1add-ac06-4134-a2fd-aff13d8c4c15)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
