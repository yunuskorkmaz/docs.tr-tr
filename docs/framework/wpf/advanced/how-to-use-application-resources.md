---
title: 'Nasıl yapılır: Uygulama Kaynaklarını Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- application resources [WPF]
- resources [WPF], application resources
ms.assetid: 507ea937-5191-406b-8797-0a3d9f94156d
ms.openlocfilehash: 4305c49c4322d164e2481c1508dda7c038c14694
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544163"
---
# <a name="how-to-use-application-resources"></a>Nasıl yapılır: Uygulama Kaynaklarını Kullanma
Bu örnek uygulama kaynaklarının nasıl kullanılacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir uygulama tanımı dosyası gösterir. Uygulama tanımı dosyası bir kaynak bölümü tanımlar (için bir değer <xref:System.Windows.Application.Resources%2A> özelliği). Uygulama düzeyinde tanımlanan kaynaklara uygulamanın parçası olan diğer tüm sayfalar tarafından erişilebilir. Bu durumda, bildirilen stili kaynaktır. Bir denetim şablonu içeren tam bir stil uzun olabileceğinden, bu örnek içinde tanımlanan denetim şablonunu atlar <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> özellik ayarlayıcısı stili.  
  
 [!code-xaml[ResourcesApplication#PreTemplateResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#pretemplateresource)]  
[!code-xaml[ResourcesApplication#PostTemplateResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#posttemplateresource)]  
  
 Aşağıdaki örnekte gösterildiği bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] önceki örnekte tanımlanan uygulama düzeyi kaynağa başvuran sayfa. Kaynağı kullanarak başvurulan bir [StaticResource biçimlendirme uzantısı](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) benzersiz kaynak anahtarı istenen kaynağın belirtir. İstenen kaynak için kaynak arama kapsamı geçerli sayfanın dışında ve tanımlanan uygulama düzeyi kaynakları olarak çalışmaya devam etmesi için hiçbir kaynak anahtarı "GelButton" olan geçerli sayfa bulunamadı.  
  
 [!code-xaml[ResourcesApplication#ConsumingPage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/page1.xaml#consumingpage)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XAML Kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Uygulama Yönetimine Genel Bakış](../../../../docs/framework/wpf/app-development/application-management-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)
