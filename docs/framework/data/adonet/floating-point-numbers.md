---
title: Kayan Noktalı Sayılar
ms.date: 03/30/2017
ms.assetid: 73c218c6-1c44-4402-a167-4f6262629a91
ms.openlocfilehash: aae7bd2ea6b5ba7bc9c69b99c93b62ba7a413d59
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033988"
---
# <a name="floating-point-numbers"></a>Kayan Noktalı Sayılar
Bu konuda kayan nokta sayıları ile çalışırken, geliştiricilerin sık karşılaştığınız sorunları bazıları açıklanmaktadır [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]. Bu sorunları şekilde bilgisayarları kayan nokta sayıları depolamak ve gibi belirli bir sağlayıcıya özgü olmayan neden olduğu <xref:System.Data.SqlClient> veya <xref:System.Data.OracleClient>.  
  
 Kayan nokta sayıları genellikle tam bir ikili gösterim gerekmez. Bunun yerine, bilgisayar sayısı yaklaşık olarak depolar. Farklı zamanlarda farklı sayıda ikili basamak sayıyı temsil etmek için kullanılabilir. Kayan zaman noktası numarası, başka bir gösterimiyse, bu sayının en az anlamlı basamaklarında bir gösterimden dönüştürülür biraz farklılık gösterebilir. Dönüştürme, genellikle numarası bir türden diğerine başka bir türe dönüştürüldüğüne oluşur. Değişim dönüştürme türleri veya veritabanı değerlerini temsil eden türleri arasında bir veritabanı içinde oluşup oluşmadığını gerçekleşir. Bu değişiklikler nedeniyle, mantıksal olarak eşit olacaktır sayıları farklı değerlere sahip neden, en az önemli basamak değişiklikler olabilir. Duyarlık sayısı basamak sayısı, beklenenden daha küçük veya çok büyük olabilir. Sayı, dize olarak biçimlendirilmiş, beklenen değerle gösterilmeyebilir.  
  
 Bu etkileri en aza indirmek için kullanabileceğiniz sayısal türler arasında en yakın eşleşme kullanmanız gerekir. Örneğin, SQL Server ile çalışıyorsanız, kayan nokta türünde bir değer için bir Transact-SQL değerini gerçek tür dönüştürürseniz, tam bir sayısal değer değişebilir. İçinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], dönüştürme bir <xref:System.Single> için bir <xref:System.Double> da beklenmeyen sonuçlara neden olabilir. Her iki durumda, iyi bir stratejisi tüm değerleri uygulama kullanımı aynı sayısal türü olmasını sağlamaktır. Bir sabit duyarlıklı ondalık türü kullanmak veya bunlarla çalışmadan önce kayan noktalı sayıların sabit duyarlıklı ondalık türüne dönüştürme.  
  
 Eşitlik karşılaştırma sorunları gidermek için en az anlamlı basamaklarında değişikliklere göz ardı edilir, böylece uygulamanız kodlama göz önünde bulundurun. Örneğin, iki sayıyı eşit olup olmadığını görmek için karşılaştırmak yerine başka bir sayıyı bir sayıdan çıkarır. Fark yuvarlama kabul edilebilir bir kenar boşluğu içinde ise, aynı olmaları durumunda gibi uygulamanızın sayıları davranabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kayan Noktalı Sayıların Neden Duyarlık Kaybedebileceği](/cpp/build/reference/why-floating-point-numbers-may-lose-precision)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
