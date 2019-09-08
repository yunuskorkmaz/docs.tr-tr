---
title: Güvenlik (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: 6116b2b8-75f4-4d8b-aea6-c13e55cda50b
ms.openlocfilehash: d6f00fccb0ea2f49c19b640e31d96e575c0d48b9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782787"
---
# <a name="security-linq-to-dataset"></a>Güvenlik (LINQ to DataSet)
Bu konuda LINQ to DataSet güvenlik sorunları ele alınmaktadır.  
  
## <a name="passing-a-query-to-an-untrusted-component"></a>Güvenilmeyen bir bileşene sorgu geçirme  
 Bir LINQ to DataSet sorgusu, bir programın bir noktasında formüllenebilir ve farklı bir şekilde çalıştırılabilir. Sorgunun formül altında olduğu noktada, sorgu, çağıran yöntemin ait olduğu sınıfın özel üyeleri veya yerel değişkenleri/bağımsız değişkenleri temsil eden semboller gibi söz konusu noktada görünür olan herhangi bir öğeye başvurabilir. Yürütme zamanında sorgu etkin bir şekilde sorgu tarafından başvurulan üyelere, çağıran kodun kendileriyle ilgili bir görünürlük olmasa bile bu üyelere erişebilir. Sorguyu yürüten kod, üzerinde nelerin erişebileceğini seçemediğinden rastgele eklenen görünürlüğe sahip değildir. Sorgunun ne kadar erişilebilir olduğuna ve yalnızca sorgunun kendisi aracılığıyla erişebilecektir.  
  
 Bu, bir sorguya başvuruyu, sorgunun başvurduğu tüm ortak ve özel üyelere erişim sağlayan bileşenin bir başka bir kod parçasına geçirilerek olduğunu gösterir. Genel olarak, sorgu dikkatle oluşturulmadığı için LINQ to DataSet sorguları güvenilmeyen bileşenlere geçirilmemelidir, çünkü özel tutulması gereken bilgileri açığa çıkarır.  
  
## <a name="external-input"></a>Dış giriş  
 Uygulamalar genellikle dış giriş alır (bir kullanıcı veya başka bir harici aracıdan) ve bu girişe göre eylemler gerçekleştirir.  LINQ to DataSet durumda, uygulama dış girişe göre belirli bir şekilde bir sorgu oluşturabilir veya sorgudaki dış girişi kullanabilir. LINQ to DataSet sorguları, sabit değerlerinin kabul edildiği her yerde parametreleri kabul eder. Uygulama geliştiricileri, harici bir aracıdan doğrudan sorguya ekleme değişmez değerleri yerine parametreli sorgular kullanmalıdır.  
  
 Kullanıcı veya dış aracıdan doğrudan veya dolaylı olarak türetilen tüm girişler, yetkisiz eylemler gerçekleştirmek için hedef dilin söz dizimini kullanan içeriğe sahip olabilir. Bu, hedef dilin Transact-SQL olduğu bir saldırı deseninin ardından adlandırılmış bir SQL ekleme saldırısı olarak bilinir. Doğrudan sorguya eklenen kullanıcı girişi, bir veritabanı tablosunu bırakmak, hizmet reddine neden olmak veya gerçekleştirilen işlemin doğasını değiştirmek için kullanılır. Sorgu kompozisyonu LINQ to DataSet mümkün olsa da, nesne modeli API 'SI aracılığıyla yapılır. LINQ to DataSet sorguları, Transact-SQL ' de olduklarından ve SQL ekleme saldırılarına maruz, geleneksel anlamda açık olmayan dize düzenleme veya birleştirme kullanılarak oluşmazlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Programlama Kılavuzu](programming-guide-linq-to-dataset.md)
