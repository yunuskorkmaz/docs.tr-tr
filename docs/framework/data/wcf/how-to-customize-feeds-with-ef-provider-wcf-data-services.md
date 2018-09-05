---
title: 'Nasıl yapılır: (WCF Veri Hizmetleri) Entity Framework sağlayıcısı ile akışları özelleştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: fd16272e-36f2-415e-850e-8a81f2b17525
ms.openlocfilehash: 41bbeb6536bbba3e107707ba2805a36a2c76c636
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526117"
---
# <a name="how-to-customize-feeds-with-the-entity-framework-provider-wcf-data-services"></a>Nasıl yapılır: (WCF Veri Hizmetleri) Entity Framework sağlayıcısı ile akışları özelleştirme
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bir varlığın özelliklerini AtomPub protokolünde tanımlanan kullanılmayan öğelere eşlenebilir böylece bir veri hizmeti yanıttaki Atom serileştirme özelleştirmenize olanak sağlar. Bu konuda, Entity Framework kullanarak bir .edmx dosyası içinde tanımlanan bir veri modeli varlık türleri için eşleme öznitelikleri tanımlamak gösterilmektedir. Daha fazla bilgi için [akış özelleştirme](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).  
  
 Bu konu başlığında veri modeli içeren aracı tarafından oluşturulan .edmx dosyasını el ile değiştirir. Veri modeline uzantıları varlık tasarımcısı tarafından desteklenmediğinden dosyayı el ile değiştirmeniz gerekir. Varlık veri modeli araçları oluşturan .edmx dosyası hakkında daha fazla bilgi için bkz. [.edmx dosyasını genel bakış](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4). Bu konudaki örnek Northwind örnek veri hizmeti ve otomatik olarak oluşturulan istemci veri hizmeti sınıfları kullanır. Bu hizmet ve istemci veri sınıfları tamamladığınızda oluşturulur [WCF Veri Hizmetleri Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### <a name="to-manually-modify-the-northwindedmx-file-to-add-feed-customization-attributes"></a>Akış özelleştirme öznitelikleri eklemek için Northwind.edmx dosyasını el ile değiştirme  
  
1.  İçinde **Çözüm Gezgini**, sağ `Northwind.edmx` dosya ve ardından **birlikte Aç**.  
  
2.  İçinde **birlikte Aç - Northwind.edmx** iletişim kutusunda **XML Düzenleyicisi**ve ardından **Tamam**.  
  
3.  Bulun `ConceptualModels` öğesi ve mevcut Değiştir `Customers` varlık türünü içeren aşağıdaki öğe ile akış özelleştirme eşleme öznitelikleri:  
  
     [!code-xml[Astoria Custom Feeds#EdmFeedCustomers](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/northwind.csdl#edmfeedcustomers)]  
  
4.  Değişiklikleri kaydedin ve Northwind.edmx dosyayı kapatın.  
  
5.  (İsteğe bağlı) Northwind.edmx dosyaya sağ tıklayın ve ardından **özel aracı Çalıştır**.  
  
     Bu, gerekli nesne katmanı dosyası oluşturur.  
  
6.  Projeyi yeniden derleyin.  
  
## <a name="example"></a>Örnek  
 Önceki örnekte URI'sini aşağıdaki sonucu verir `http://myservice/``Northwind.svc/Customers('ALFKI')`.  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/edmfeedresult.xml#edmfeedresult)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity Framework Sağlayıcısı](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)
