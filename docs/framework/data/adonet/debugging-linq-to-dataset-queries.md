---
title: LINQ to DataSet sorgularında hata ayıklama
ms.date: 03/30/2017
ms.assetid: f4c54015-8ce2-4c5c-8d18-7038144cc66d
ms.openlocfilehash: fd10e6c715529ba937ba09732a254d311158b0f1
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43481057"
---
# <a name="debugging-linq-to-dataset-queries"></a>LINQ to DataSet sorgularında hata ayıklama
[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] hata ayıklamayı destekler [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kod. Ancak, hata ayıklama arasındaki bazı farklar vardır [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kod ve olmayan-[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] yönetilen kod. Hata ayıklama özelliklerinin çoğu çalışmak [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] deyimleri, Adımlama, kesme noktaları ayarlama ve hata ayıklayıcı pencerelerinde gösterilen sonuçları görüntüleme. Ancak, sorgu yürütme hata ayıklama sırasında göz önünde bulundurmanız gereken bazı etkilere sahip ertelenmiş [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kod ve Düzenle ve Devam Et'i kullanmadan gereken bazı sınırlamalar vardır. Eşsiz hata ayıklama özelliklerini bu konu başlığı altında anlatılmaktadır [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] olmayan karşılaştırıldığında[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] yönetilen kod.  
  
## <a name="viewing-results"></a>Sonuçları görüntüleme  
 Sonucu görüntüleyebileceğiniz bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] DataTips, izleme penceresi ve QuickWatch iletişim kutusunu kullanarak deyimi. Bir kaynak penceresinde kullanarak, kaynak penceresinde bir sorgunun işaretçisini duraklatabilirsiniz ve bir DataTip görünür. Kopyalayıp bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] değişkenini kopyalayıp İzle penceresine veya QuickWatch iletişim kutusu yapıştırın. İçinde [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], bir sorgu oluşturulduğunda veya bildirildi, ancak yalnızca sorgu yürütüldüğünde değerlendirilmez. Bu adlandırılır *ertelenmiş yürütme*. Bu nedenle sorgu değişkeni değerlendirilene kadar bir değeri yok. Daha fazla bilgi için [LINQ to DataSet sorgularında](../../../../docs/framework/data/adonet/queries-in-linq-to-dataset.md).  
  
 Hata ayıklayıcı sorgu sonuçlarını görüntülemek için bir sorguyu değerlendirmelidir. Bu örtülü değerlendirme, görüntülediğinizde gerçekleşir bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] hata ayıklayıcı ve sorgu sonucunda önünde bulundurmanız gereken bazı etkilere sahiptir. Her değerlendirme sorgusunun zaman alır. Sonuç düğümlerinin genişletilmesi zaman alır. Bazı sorgular için yinelenen değerlendirme belirgin bir performans düşüşüyle neden olabilir. Bir sorgunun değerlendirilmesi verilerin değerinde veya programınızın durumunu yapılan değişiklikler etkilere neden olabilir. Tüm sorguların yan etkisi yoktur. Bir sorgu yan etkileri olmadan güvenli bir şekilde değerlendirilip değerlendirilmediğini belirlemek için sorguyu uygulayan kodu anlamanız gerekir. Daha fazla bilgi için [yan etkiler ve ifadeler](https://msdn.microsoft.com/library/e1f8a6ea-9e19-481d-b6bd-df120ad3bf4e).  
  
## <a name="edit-and-continue"></a>Düzenle ve Devam Et  
 Düzenle ve devam et değişiklikleri desteklemiyor [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorgular. Ekleme, kaldırma veya değiştirme, bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] deyimi hata ayıklama oturumu sırasında bir iletişim kutusu görünür bildiren değişikliğin Düzenle ve devam et tarafından desteklenmez. Bu noktada, ya değişiklikleri geri almak veya hata ayıklama oturumunu durdurmak ve düzenlenen kodla yeni bir oturumu yeniden başlatabilirsiniz.  
  
 Ayrıca, Düzenle ve devam et türü veya kullanılan bir değişkenin değerini değiştirmeyi desteklemez bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] deyimi. Yine, ya değişiklikleri geri almak veya durdurabilir ve hata ayıklama oturumunu yeniden başlatın.  
  
 Visual C# içinde Visual Studio'da Düzenle ve devam et herhangi bir kod içeren bir yöntem üzerinde kullanamazsınız bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorgu.  
  
 Visual Studio'da Visual Basic'te, Düzenle ve devam et non - üzerinde kullanabileceğiniz[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kodda bile içeren bir yöntem bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorgu. Önce kod ekleyip [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] ifadesi, satır numarası değişiklikleri etkiler olsa bile [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorgu. Visual Basic hata ayıklama deneyimi için olmayan[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kodu kalır, aynı, önce olduğu gibi [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kullanıma sunulmuştur. Size, Ekle, Kaldır veya değiştiremediğiniz bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] değişiklikleri uygulamak için hata ayıklama durdurmadığınız sürece, ancak sorgu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen Kodda Hata Ayıklama](/visualstudio/debugger/debugging-managed-code)  
 [Programlama Kılavuzu](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
