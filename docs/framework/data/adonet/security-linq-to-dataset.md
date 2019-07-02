---
title: Güvenlik (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: 6116b2b8-75f4-4d8b-aea6-c13e55cda50b
ms.openlocfilehash: 33af2200c5d672dc63dc7be79833a174bfe31c20
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504262"
---
# <a name="security-linq-to-dataset"></a>Güvenlik (LINQ to DataSet)
Bu konuda, LINQ to DataSet güvenlik sorunlarını ele alınmıştır.  
  
## <a name="passing-a-query-to-an-untrusted-component"></a>Güvenilmeyen bir bileşeni için bir sorgu geçirme  
 Bir LINQ to DataSet sorgu, tek bir program noktasında şeklide ve başka bir yürütülür. Sorguyu formüle nerede bir noktada sorgu gibi özel üyeler çağıran Metoda ait olduğu sınıfın veya yerel değişkenler/bağımsız değişkenlerini temsil eden simgeler görünür olup bu noktada, herhangi bir öğe başvurabilirsiniz. Yürütme sırasında sorgu etkili bir şekilde çağıran kod, bunları görünürlüğe sahip olmayacağı olsa bile, oluşumunu sorgu tarafından başvurulan bu üyelere erişmek mümkün olacaktır. Ne erişmek seçemezsiniz, rastgele ek görünürlük, sorguyu yürüten bir kod yok. Hangi sorgu erişir, kesinlikle erişebilir ve yalnızca sorgunun kendisi aracılığıyla.  
  
 Bu bileşenin başka bir kod parçası için bir sorgu için bir başvuru geçirerek sorgu alma erişimle tüm ortak ve özel üyeler, sorgunun başvurduğu güvenildiğini anlamına gelir. Genel olarak, böylece özel tutulması gereken bilgileri açığa çıkarmamak sorgu dikkatli bir şekilde yapılandırılmış sürece LINQ to DataSet sorgularında güvenilmeyen bileşenlere geçirilmemelidir.  
  
## <a name="external-input"></a>Dış giriş  
 Uygulamalar genellikle dış girişi (bir kullanıcı veya başka bir dış aracı) alan ve bu giriş temelinde eylemleri gerçekleştirebilirsiniz.  Uygulama, söz konusu olduğunda LINQ to DataSet Sorguda Dış giriş veya giriş sorguda kullanmak dış göre belirli bir şekilde oluşturulabilir. LINQ to DataSet sorgularında kabul parametreleri her yerde değişmez değerler kabul edilir. Uygulama geliştiricileri, sorguyu doğrudan parametreli sorgular yerine bir dış aracı ekleme değişmez kullanmanız gerekir.  
  
 Tüm giriş doğrudan veya dolaylı olarak bir kullanıcı veya bir dış aracı türetilmiş izinsiz eylemler gerçekleştirmek için hedef dilinin sözdizimi yararlanan içerik olabilir. Bu, hedef dil Transact-SQL olduğu bir saldırı desenini sonra adlandırılmış bir SQL ekleme saldırısına olarak bilinir. Kullanıcı girişi sorguyu doğrudan eklenen bir veritabanı tablosu bırakın, hizmet reddine neden veya aksi halde gerçekleştirilmekte olan işlemin yapısını değiştirmek için kullanılır. Sorgu oluşturma LINQ to DataSet mümkün olsa da, bu nesne modeli API aracılığıyla gerçekleştirilir. LINQ to DataSet sorgularında değil oluşan dize düzenlemesi veya birleştirme kullanarak olan Transact-SQL ve SQL ekleme saldırılarına karşı geleneksel anlamda fazla etkilenmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Programlama Kılavuzu](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
