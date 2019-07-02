---
title: LINQ to DataSet Sorgularında Hata Ayıklama
ms.date: 03/30/2017
ms.assetid: f4c54015-8ce2-4c5c-8d18-7038144cc66d
ms.openlocfilehash: 38eda9f352c4a8d8590e5e57b48c694eadd0397b
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67503988"
---
# <a name="debugging-linq-to-dataset-queries"></a>LINQ to DataSet Sorgularında Hata Ayıklama

Visual Studio LINQ hata ayıklama için veri kümesi kodunu destekler. Ancak, veri kümesi kodunu ve olmayan-LINQ to DataSet yönetilen kod için LINQ hata ayıklama arasındaki bazı farklar vardır. Hata ayıklama özelliklerinin çoğu LINQ ile Adımlama, kesme noktaları ayarlama ve hata ayıklayıcı pencerelerinde gösterilen sonuçları görüntüleme dahil olmak üzere, veri kümesi deyimleri için çalışır. Ancak, ertelenen sorgu yürütme için veri kümesi kodunu LINQ hata ayıklama sırasında göz önünde bulundurmanız gereken bazı etkilere sahiptir ve Düzenle ve Devam Et'i kullanmadan gereken bazı sınırlamalar vardır. Bu konu LINQ to DataSet olmayan-LINQ to DataSet yönetilen kod ile karşılaştırıldığında eşsiz hata ayıklama özelliklerini açıklar.  
  
## <a name="viewing-results"></a>Sonuçları görüntüleme  
 DataTips, izleme penceresi ve QuickWatch iletişim kutusunu kullanarak, bir LINQ to DataSet deyimi sonucunu görüntüleyebilirsiniz. Bir kaynak penceresinde kullanarak, kaynak penceresinde bir sorgunun işaretçisini duraklatabilirsiniz ve bir DataTip görünür. LINQ to DataSet değişkene kopyalayın ve İzle penceresine veya QuickWatch iletişim kutusu yapıştırın. LINQ to DataSet, bir sorgu oluşturulduğunda veya bildirildi, ancak yalnızca sorgu yürütüldüğünde değerlendirilmez. Bu adlandırılır *ertelenmiş yürütme*. Bu nedenle sorgu değişkeni değerlendirilene kadar bir değeri yok. Daha fazla bilgi için [LINQ to DataSet sorgularında](../../../../docs/framework/data/adonet/queries-in-linq-to-dataset.md).  
  
 Hata ayıklayıcı sorgu sonuçlarını görüntülemek için bir sorguyu değerlendirmelidir. Hata ayıklayıcıda bir LINQ to DataSet sorgu sonucunu görüntüleyin ve dikkate almanız gereken bazı etkilere sahip bu örtülü değerlendirme gerçekleşir. Her değerlendirme sorgusunun zaman alır. Sonuç düğümlerinin genişletilmesi zaman alır. Bazı sorgular için yinelenen değerlendirme belirgin bir performans düşüşüyle neden olabilir. Bir sorgunun değerlendirilmesi verilerin değerinde veya programınızın durumunu yapılan değişiklikler etkilere neden olabilir. Tüm sorguların yan etkisi yoktur. Bir sorgu yan etkileri olmadan güvenli bir şekilde değerlendirilip değerlendirilmediğini belirlemek için sorguyu uygulayan kodu anlamanız gerekir. Daha fazla bilgi için [yan etkiler ve ifadeler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/a7a250bs(v=vs.120)).  
  
## <a name="edit-and-continue"></a>Düzenle ve Devam Et  
 Düzenle ve devam et, LINQ to DataSet sorgularında değişiklikleri desteklemez. Ekleyin, kaldırın veya bir LINQ hata ayıklama oturumu sırasında veri kümesi deyimi değiştirin değişikliğin Düzenle ve devam et tarafından desteklenmeyen bildiren bir iletişim kutusu görüntülenir. Bu noktada, ya değişiklikleri geri almak veya hata ayıklama oturumunu durdurmak ve düzenlenen kodla yeni bir oturumu yeniden başlatabilirsiniz.  
  
 Ayrıca, Düzenle ve devam et, türü veya bir LINQ to DataSet deyimi kullanılan bir değişkenin değerini değiştirmeyi desteklemez. Yine, ya değişiklikleri geri almak veya durdurabilir ve hata ayıklama oturumunu yeniden başlatın.  
  
 Görselde C# Visual Studio'da Düzenle ve devam et bir LINQ to DataSet sorgu içeren bir yöntem herhangi bir kod üzerinde kullanamazsınız.  
  
 Visual Studio'da Visual Basic'te, LINQ olmayan veri kümesi kodunda bile bir LINQ to DataSet sorgu içeren bir yöntem üzerinde Düzenle ve devam et kullanabilirsiniz. LINQ to DataSet deyimi, önce kod değişiklikleri LINQ to DataSet sorgu satır numarasını etkilese kaldırın ya da ekleyin. LINQ to DataSet sunulmadan önce olduğu gibi Visual Basic hata ayıklama deneyimi olmayan-LINQ to DataSet kod için aynı kalır. Değiştirme, ekleme veya değişiklikleri uygulamak için hata ayıklamayı durdurmak sürece bir LINQ to DataSet sorgusunda, ancak kaldırma olamaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen Kodda Hata Ayıklama](/visualstudio/debugger/debugging-managed-code)
- [Programlama Kılavuzu](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
