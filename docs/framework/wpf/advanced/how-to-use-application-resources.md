---
title: 'Nasıl yapılır: Uygulama Kaynaklarını Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- application resources [WPF]
- resources [WPF], application resources
ms.assetid: 507ea937-5191-406b-8797-0a3d9f94156d
ms.openlocfilehash: acd172448ebdefd6395feec6ad50e1c9491d9e27
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54733603"
---
# <a name="how-to-use-application-resources"></a>Nasıl yapılır: Uygulama Kaynaklarını Kullanma
Bu örnek, uygulama kaynaklarının nasıl kullanılacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir uygulama tanımı dosyası gösterir. Uygulama tanımı dosyası kaynak bölüm tanımlar (için bir değer <xref:System.Windows.Application.Resources%2A> özelliği). Uygulama düzeyinde tanımlanan kaynaklar, uygulamanın parçası olan diğer tüm sayfalar tarafından erişilebilir. Bu durumda, bildirilen stili kaynaktır. Bir denetim şablonu içeren tam bir stil uzun bu nedenle, bu örnek içinde tanımlanan bir denetim şablonu atlar <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> özellik ayarlayıcısına stili.  
  
 [!code-xaml[ResourcesApplication#PreTemplateResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#pretemplateresource)]  
[!code-xaml[ResourcesApplication#PostTemplateResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#posttemplateresource)]  
  
 Aşağıdaki örnekte gösterildiği bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] önceki örnekte tanımlanan uygulama düzeyi kaynağa başvuran sayfa. Kaynak kullanarak başvurulan bir [StaticResource işaretleme uzantısı](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) , istenen kaynağın benzersiz kaynak anahtarını belirtir. Kaynak arama kapsamı istenen kaynak için geçerli sayfanın dışında ve tanımlı uygulama düzeyi kaynakları içine devam eder "GelButton" anahtarı ile kaynak geçerli sayfada bulunur.  
  
 [!code-xaml[ResourcesApplication#ConsumingPage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/page1.xaml#consumingpage)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [XAML Kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md)
- [Uygulama Yönetimine Genel Bakış](../../../../docs/framework/wpf/app-development/application-management-overview.md)
- [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)
