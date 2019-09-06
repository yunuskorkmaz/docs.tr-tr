---
title: Kayan Noktalı Sayılar
ms.date: 03/30/2017
ms.assetid: 73c218c6-1c44-4402-a167-4f6262629a91
ms.openlocfilehash: 1f76a6ab8cc2a44580229014dd8ebae6b317921f
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2019
ms.locfileid: "70374425"
---
# <a name="floating-point-numbers"></a>Kayan Noktalı Sayılar
Bu konuda, ADO.NET ' de kayan nokta numaralarıyla çalışırken geliştiricilerin sıkça karşılaştığı bazı sorunlar açıklanmaktadır. Bu sorunlar, bilgisayarların kayan nokta numaralarını saklamasının ve <xref:System.Data.SqlClient> ya <xref:System.Data.OracleClient>da gibi belirli bir sağlayıcıya özgü olmayan şekilde kaynaklanmasından kaynaklanmıştır.  
  
 Kayan nokta numaraları genellikle tam bir ikili gösterimine sahip değildir. Bunun yerine, bilgisayar sayının yaklaşık bir kısmını depolar. Farklı zamanlarda, sayıyı temsil etmek için farklı sayıda ikili basamak kullanılabilir. Bir kayan nokta numarası bir gösterimden başka bir gösterime dönüştürüldüğünde, bu sayının en az önemli hanesi biraz farklılık gösterebilir. Dönüştürme genellikle, sayı bir türden başka bir türe yayınlanarak oluşur. Değişim, dönüştürmenin bir veritabanı içinde oluşup oluşmadığını, veritabanı değerlerini temsil eden türler arasında veya türler arasında meydana gelir. Bu değişiklikler nedeniyle, mantıksal olarak eşit olacak sayılar, farklı değerlere sahip olmalarını sağlamak için en az önemli rakamlarla değişiklik gösterebilir. Sayıdaki duyarlık basamak sayısı beklenenden daha büyük veya daha küçük olabilir. Dize olarak biçimlendirilirken, sayı beklenen değeri gösteremeyebilir.  
  
 Bu etkileri en aza indirmek için, sizin için kullanılabilen sayısal türler arasında en yakın eşleşmeyi kullanmanız gerekir. Örneğin, SQL Server çalışıyorsanız, gerçek türdeki bir Transact-SQL değerini float türünde bir değere dönüştürürseniz, tam sayısal değer değişebilir. .NET Framework, bir <xref:System.Single> <xref:System.Double> ' a dönüştürmek beklenmedik sonuçlara neden olabilir. Her iki durumda da, uygulamadaki tüm değerlerin aynı sayısal türü kullanmasını sağlamak iyi bir stratejidir. Ayrıca, sabit duyarlıklı ondalık bir tür kullanabilir veya bunlarla çalışabilmeniz için kayan nokta sayılarını sabit duyarlığa dönüştürme türüne çevirebilirsiniz.  
  
 Eşitlik karşılaştırmasıyla ilgili sorunları çözmek için, en az önemli basamaklı değişimlerin yoksayılması için uygulamanızı kodlamayı göz önünde bulundurun. Örneğin, iki sayının eşit olup olmadığını görmek için, başka bir sayıdan bir sayı çıkarın. Fark, yuvarlama için kabul edilebilir bir kenar boşluğu içindeyse, uygulamanız sayıları aynı gibi kabul edebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kayan Noktalı Sayıların Neden Duyarlık Kaybedebileceği](/cpp/build/why-floating-point-numbers-may-lose-precision)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
