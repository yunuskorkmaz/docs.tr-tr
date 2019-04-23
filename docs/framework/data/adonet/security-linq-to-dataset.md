---
title: Güvenlik (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: 6116b2b8-75f4-4d8b-aea6-c13e55cda50b
ms.openlocfilehash: aa281cb4d6019ca2df85137eb505724e55b8060a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59087345"
---
# <a name="security-linq-to-dataset"></a>Güvenlik (LINQ to DataSet)
Bu konuda bulunan güvenlik sorunlarını ele alınmaktadır [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].  
  
## <a name="passing-a-query-to-an-untrusted-component"></a>Güvenilmeyen bir bileşeni için bir sorgu geçirme  
 A [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorgu programının bir noktasında şeklide ve başka bir yürütülebilir. Sorguyu formüle nerede bir noktada sorgu gibi özel üyeler çağıran Metoda ait olduğu sınıfın veya yerel değişkenler/bağımsız değişkenlerini temsil eden simgeler görünür olup bu noktada, herhangi bir öğe başvurabilirsiniz. Yürütme sırasında sorgu etkili bir şekilde çağıran kod, bunları görünürlüğe sahip olmayacağı olsa bile, oluşumunu sorgu tarafından başvurulan bu üyelere erişmek mümkün olacaktır. Ne erişmek seçemezsiniz, rastgele ek görünürlük, sorguyu yürüten bir kod yok. Hangi sorgu erişir, kesinlikle erişebilir ve yalnızca sorgunun kendisi aracılığıyla.  
  
 Bu bileşenin başka bir kod parçası için bir sorgu için bir başvuru geçirerek sorgu alma erişimle tüm ortak ve özel üyeler, sorgunun başvurduğu güvenildiğini anlamına gelir. Genel olarak, [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorguları geçirilemez güvenilmeyen bileşenleri, böylece özel tutulması gereken bilgileri açığa çıkarmamak sorgu dikkatli bir şekilde yapılandırılmış sürece.  
  
## <a name="external-input"></a>Dış giriş  
 Uygulamalar genellikle dış girişi (bir kullanıcı veya başka bir dış aracı) alan ve bu giriş temelinde eylemleri gerçekleştirebilirsiniz.  Durumunda, [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], uygulama bir sorgu dış giriş veya giriş sorguda kullanmak dış göre belirli bir şekilde oluşturulabilir. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorgular, her yerde değişmez değerleri kabul edildiğini parametreleri kabul eder. Uygulama geliştiricileri, sorguyu doğrudan parametreli sorgular yerine bir dış aracı ekleme değişmez kullanmanız gerekir.  
  
 Tüm giriş doğrudan veya dolaylı olarak bir kullanıcı veya bir dış aracı türetilmiş izinsiz eylemler gerçekleştirmek için hedef dilinin sözdizimi yararlanan içerik olabilir. Bu, hedef dil Transact-SQL olduğu bir saldırı desenini sonra adlandırılmış bir SQL ekleme saldırısına olarak bilinir. Kullanıcı girişi sorguyu doğrudan eklenen bir veritabanı tablosu bırakın, hizmet reddine neden veya aksi halde gerçekleştirilmekte olan işlemin yapısını değiştirmek için kullanılır. Sorgu oluşturmak mümkün olsa da [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], nesne modeli API aracılığıyla gerçekleştirilir. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dize düzenlemesi veya birleştirme, bunlar Transact-SQL ve SQL ekleme saldırılarına karşı geleneksel anlamda fazla etkilenmez gibi kullanarak sorguları oluşur değil.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Programlama Kılavuzu](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
