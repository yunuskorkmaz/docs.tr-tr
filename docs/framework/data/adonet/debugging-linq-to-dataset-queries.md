---
title: LINQ to DataSet Sorgularında Hata Ayıklama
ms.date: 03/30/2017
ms.assetid: f4c54015-8ce2-4c5c-8d18-7038144cc66d
ms.openlocfilehash: 5f6e711d13a71f73a75e774c9251c5c29216b860
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554354"
---
# <a name="debugging-linq-to-dataset-queries"></a>LINQ to DataSet Sorgularında Hata Ayıklama

Visual Studio LINQ to DataSet kodun hata ayıklamasını destekler. Ancak, hata ayıklama LINQ to DataSet kodu ve LINQ to DataSet olmayan yönetilen kod arasında bazı farklılıklar vardır. Çoğu hata ayıklama özelliği, atlama, kesme noktaları ayarlama ve hata ayıklayıcı penceresinde gösterilen sonuçları görüntüleme dahil LINQ to DataSet deyimleriyle çalışır. Bununla birlikte, içinde ertelenmiş sorgu yürütmesinin LINQ to DataSet kodda hata ayıklarken göz önünde bulundurmanız gereken bazı yan etkileri vardır ve Düzenle ve devam et kullanımı ile ilgili bazı sınırlamalar vardır. Bu konuda, LINQ to DataSet yönetilen kod ile karşılaştırıldığında LINQ to DataSet için benzersiz hata ayıklamanın yönleri açıklanmaktadır.  
  
## <a name="viewing-results"></a>Sonuçları görüntüleme  
 LINQ to DataSet deyimin sonucunu, DataTips, izleme penceresi ve QuickWatch iletişim kutusunu kullanarak görüntüleyebilirsiniz. Kaynak pencereyi kullanarak işaretçiyi kaynak penceresinde bir sorgu üzerinde duraklatabilir ve bir DataTip belirir. Bir LINQ to DataSet değişkenini kopyalayabilir ve izleme penceresi veya QuickWatch iletişim kutusuna yapıştırabilirsiniz. LINQ to DataSet, bir sorgu oluşturulduğunda veya bildirildiğinde, ancak yalnızca sorgu yürütüldüğünde değerlendirilmez. Bu, *ertelenmiş yürütme*olarak adlandırılır. Bu nedenle, sorgu değişkeni değerlendirilene kadar bir değere sahip değildir. Daha fazla bilgi için bkz. [LINQ to DataSet sorguları](queries-in-linq-to-dataset.md).  
  
 Hata ayıklayıcı sorgu sonuçlarını göstermek için bir sorguyu değerlendirmelidir. Bu örtük değerlendirme hata ayıklayıcıda LINQ to DataSet bir sorgu sonucu görüntülediğinizde oluşur ve göz önünde bulundurmanız gereken bazı etkileri vardır. Sorgunun her değerlendirmesi zaman alır. Sonuçlar düğümünü genişletme zaman alır. Bazı sorgular için yinelenen değerlendirme, dikkat çekici bir performans cezasına neden olabilir. Bir sorguyu değerlendirmek, verilerin değerinde veya programınızın durumunda değişiklik gösteren yan etkilere neden olabilir. Tüm sorguların yan etkileri yoktur. Bir sorgunun yan etkileri olmadan güvenle değerlendirilemeyeceğini anlamak için sorguyu uygulayan kodu anlamanız gerekir. Daha fazla bilgi için bkz. [yan etkiler ve ifadeler](/previous-versions/visualstudio/visual-studio-2013/a7a250bs(v=vs.120)).  
  
## <a name="edit-and-continue"></a>Düzenle ve Devam Et  
 Düzenle ve devam et, LINQ to DataSet sorgularda yapılan değişiklikleri desteklemez. Hata ayıklama oturumu sırasında bir LINQ to DataSet ifadesi ekler, kaldırır veya değiştirirseniz, değişikliğin Düzenle ve devam et tarafından desteklenmediğini belirten bir iletişim kutusu görüntülenir. Bu noktada, değişiklikleri geri alabilir ya da hata ayıklama oturumunu durdurabilir ve düzenlenmiş kodla yeni bir oturumu yeniden başlatabilirsiniz.  
  
 Ayrıca, Düzenle ve devam et, LINQ to DataSet ifadesinde kullanılan bir değişkenin türünü veya değerini değiştirmeyi desteklemez. Yine, değişiklikleri geri alabilir veya hata ayıklama oturumunu durdurup yeniden başlatabilirsiniz.  
  
 Visual Studio 'Da Visual C# ' de, LINQ to DataSet sorgusu içeren bir yöntemde Düzenle ve devam et kullanamazsınız.  
  
 Visual Studio 'daki Visual Basic, LINQ to DataSet bir sorgu içeren bir yöntemde bile Düzenle ve LINQ to DataSet olmayan kodda devam et ' i kullanabilirsiniz. Değişiklikler LINQ to DataSet sorgusunun satır numarasını etkilese bile LINQ to DataSet deyimden önce kod ekleyebilir veya kaldırabilirsiniz. LINQ to DataSet olmayan kod için Visual Basic hata ayıklama deneyimi LINQ to DataSet kullanılmaya başlanmadan önceki gibi kalır. Değişiklikleri uygulamak için hata ayıklamayı durdurmadığınız müddetçe, LINQ to DataSet sorgusunu değiştiremezsiniz, ekleyemez veya kaldıramazsınız.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen Kodda Hata Ayıklama](/visualstudio/debugger/debugging-managed-code)
- [Programlama Kılavuzu](programming-guide-linq-to-dataset.md)
