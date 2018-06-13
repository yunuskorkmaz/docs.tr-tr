---
title: LINQ-DataSet sorguları hata ayıklama
ms.date: 03/30/2017
ms.assetid: f4c54015-8ce2-4c5c-8d18-7038144cc66d
ms.openlocfilehash: c0d3347358fa3417f8b73fd848b4091fe7d74a15
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760121"
---
# <a name="debugging-linq-to-dataset-queries"></a>LINQ-DataSet sorguları hata ayıklama
[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] hata ayıklama destekleyen [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kodu. Ancak, hata ayıklama arasındaki bazı farklar vardır [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kod ve olmayan-[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] yönetilen kod. Hata ayıklama özelliklerinin çoğu çalışmak [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] deyimleri, Adımlama, kesme noktalarını ayarlama ve hata ayıklayıcı pencerelerinde gösterilen sonuçları görüntüleme gibi. Ancak, sorgu yürütme hata ayıklama sırasında dikkate almanız gereken bazı yan etkileri olan ertelenmiş [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kod ve Düzenle ve devam et kullanmanın bazı sınırlamalar vardır. Bu konuda ele alınmıştır özgü hata ayıklama yönlerini [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] karşılaştırıldığında olmayan[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] yönetilen kod.  
  
## <a name="viewing-results"></a>Sonuçları görüntüleme  
 Sonucu görüntüleyebileceğiniz bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] DataTips, Gözcü penceresi ve QuickWatch iletişim kutusunu kullanarak deyimi. Bir kaynak penceresini kullanarak kaynak penceresini sorguda işaretçisini duraklatabilirsiniz ve bir DataTip görüntülenir. Kopyalayabilirsiniz bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] değişkeni ve Gözcü penceresi veya QuickWatch iletişim kutusu yapıştırın. İçinde [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], bir sorgu oluşturulduğunda veya bildirildi, ancak yalnızca sorgu çalıştırıldığında değerlendirilmez. Bu adlı *yürütme ertelenmiş*. Bu nedenle, onu değerlendirilir kadar sorgu değişkenine bir değer yok. Daha fazla bilgi için bkz: [LINQ-DataSet sorgularda](../../../../docs/framework/data/adonet/queries-in-linq-to-dataset.md).  
  
 Hata ayıklayıcı sorgu sonuçlarını görüntülemek için bir sorgu değerlendirmeniz gerekir. Görüntülediğinizde bu örtük değerlendirme oluşur bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] hata ayıklayıcı ve bu sorgu sonucu sahip bulundurmanız gereken bazı etkiler. Her değerlendirme sorgusunun zaman alır. Sonuçları düğümü genişletmek zaman alır. Bazı sorgular için yinelenen değerlendirme belirgin performans cezası neden olabilir. Bir sorgu değerlendirme veri veya programınız durumunu değerini yapılan değişiklikler yan etkileri neden olabilir. Tüm sorguları yan etkileri olabilir. Bir sorgu yan etkileri güvenli bir şekilde değerlendirilebilir olup olmadığını belirlemek için sorgu uygulayan kod anlamanız gerekir. Daha fazla bilgi için bkz: [yan etkiler ve ifadeler](http://msdn.microsoft.com/library/e1f8a6ea-9e19-481d-b6bd-df120ad3bf4e).  
  
## <a name="edit-and-continue"></a>Düzenle ve Devam Et  
 Düzenle ve devam et değişiklikler desteklemiyor [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorgular. Ekleme, kaldırma veya değiştirme, bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] deyimi bir hata ayıklama oturumu sırasında bir iletişim kutusu görünür bildiren değişikliği Düzenle ve devam et tarafından desteklenmiyor. Bu noktada, ya da değişiklikleri geri almak veya hata ayıklama oturumu durdurabilir ve düzenlenen kod yeni bir oturumla yeniden başlatın.  
  
 Ayrıca, Düzenle ve devam et türü veya kullanılan bir değişkenin değerini değiştirmeyi desteklemez bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] deyimi. Yeniden ya da değişiklikleri geri almak veya durdurmak ve hata ayıklama oturumu yeniden başlatabilirsiniz.  
  
 Visual C# ile Visual Studio'da Düzenle ve devam et herhangi kodu içeren bir yöntem kullanarak bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorgu.  
  
 Visual Studio'da Visual Basic'te Düzenle ve devam et olmayan üzerinde kullanabileceğiniz[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kodda bile içeren bir yöntem bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorgu. Önce kod ekleyip [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] ifadesi, satır numarası değişiklikler etkiler olsa bile [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorgu. Visual Basic deneyimi için hata ayıklama olmayan[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kodu aynı kalır önce olduğu gibi [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sunulmuştur. Size, Ekle, Kaldır veya değiştiremediğiniz bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] değişiklikleri uygulamak için hata ayıklamayı durdurun sürece, ancak sorgu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen kodda hata ayıklama](/visualstudio/debugger/debugging-managed-code)  
 [Programlama Kılavuzu](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
