---
title: Kayan nokta sayıları
ms.date: 03/30/2017
ms.assetid: 73c218c6-1c44-4402-a167-4f6262629a91
ms.openlocfilehash: 2ab583a07c78cfa06ac597c369486f89e19ca66e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43466097"
---
# <a name="floating-point-numbers"></a>Kayan nokta sayıları
Bu konuda kayan nokta sayıları ile çalışırken, geliştiricilerin sık karşılaştığınız sorunları bazıları açıklanmaktadır [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]. Bu sorunları şekilde bilgisayarları kayan nokta sayıları depolamak ve gibi belirli bir sağlayıcıya özgü olmayan neden olduğu <xref:System.Data.SqlClient> veya <xref:System.Data.OracleClient>.  
  
 Kayan nokta sayıları genellikle tam bir ikili gösterim gerekmez. Bunun yerine, bilgisayar sayısı yaklaşık olarak depolar. Farklı zamanlarda farklı sayıda ikili basamak sayıyı temsil etmek için kullanılabilir. Kayan zaman noktası numarası, başka bir gösterimiyse, bu sayının en az anlamlı basamaklarında bir gösterimden dönüştürülür biraz farklılık gösterebilir. Dönüştürme, genellikle numarası bir türden diğerine başka bir türe dönüştürüldüğüne oluşur. Değişim dönüştürme türleri veya veritabanı değerlerini temsil eden türleri arasında bir veritabanı içinde oluşup oluşmadığını gerçekleşir. Bu değişiklikler nedeniyle, mantıksal olarak eşit olacaktır sayıları farklı değerlere sahip neden, en az önemli basamak değişiklikler olabilir. Duyarlık sayısı basamak sayısı, beklenenden daha küçük veya çok büyük olabilir. Sayı, dize olarak biçimlendirilmiş, beklenen değerle gösterilmeyebilir.  
  
 Bu etkileri en aza indirmek için kullanabileceğiniz sayısal türler arasında en yakın eşleşme kullanmanız gerekir. Örneğin, SQL Server ile çalışıyorsanız, kayan nokta türünde bir değer için bir Transact-SQL değerini gerçek tür dönüştürürseniz, tam bir sayısal değer değişebilir. İçinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], dönüştürme bir <xref:System.Single> için bir <xref:System.Double> da beklenmeyen sonuçlara neden olabilir. Her iki durumda, iyi bir stratejisi tüm değerleri uygulama kullanımı aynı sayısal türü olmasını sağlamaktır. Bir sabit duyarlıklı ondalık türü kullanmak veya bunlarla çalışmadan önce kayan noktalı sayıların sabit duyarlıklı ondalık türüne dönüştürme.  
  
 Eşitlik karşılaştırma sorunları gidermek için en az anlamlı basamaklarında değişikliklere göz ardı edilir, böylece uygulamanız kodlama göz önünde bulundurun. Örneğin, iki sayıyı eşit olup olmadığını görmek için karşılaştırmak yerine başka bir sayıyı bir sayıdan çıkarır. Fark yuvarlama kabul edilebilir bir kenar boşluğu içinde ise, aynı olmaları durumunda gibi uygulamanızın sayıları davranabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kayan Noktalı Sayıların Neden Duyarlık Kaybedebileceği](https://msdn.microsoft.com/library/1acb1add-ac06-4134-a2fd-aff13d8c4c15)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
