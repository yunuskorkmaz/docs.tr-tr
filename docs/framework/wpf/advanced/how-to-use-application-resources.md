---
title: 'Nasıl yapılır: Uygulama Kaynaklarını Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- application resources [WPF]
- resources [WPF], application resources
ms.assetid: 507ea937-5191-406b-8797-0a3d9f94156d
ms.openlocfilehash: e4114466fa8016f8e31100d7a37038b0abfdccca
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460263"
---
# <a name="how-to-use-application-resources"></a>Nasıl yapılır: Uygulama Kaynaklarını Kullanma
Bu örnek, uygulama kaynaklarının nasıl kullanılacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir uygulama tanımı dosyası gösterir. Uygulama tanımı dosyası bir kaynak bölümü tanımlar (<xref:System.Windows.Application.Resources%2A> özelliği için bir değer). Uygulama düzeyinde tanımlanan kaynaklara uygulamanın parçası olan diğer tüm sayfalar erişebilir. Bu durumda, kaynak tanımlanmış bir stildir. Bir denetim şablonu içeren bir bütün stil uzun sürebileceğinden, bu örnek stilin <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> Özellik ayarlayıcısı içinde tanımlanan denetim şablonunu atlar.  
  
 [!code-xaml[ResourcesApplication#PreTemplateResource](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#pretemplateresource)]  
[!code-xaml[ResourcesApplication#PostTemplateResource](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#posttemplateresource)]  
  
 Aşağıdaki örnekte, önceki örneğin tanımladığı uygulama düzeyi kaynağına başvuran bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfası gösterilmektedir. Kaynağa, istenen kaynak için benzersiz kaynak anahtarını belirten bir [StaticResource Işaretleme uzantısı](staticresource-markup-extension.md) kullanılarak başvurulur. Geçerli sayfada "GelButton" anahtarına sahip hiçbir kaynak bulunamadı. bu nedenle, istenen kaynak için kaynak arama kapsamı geçerli sayfanın ötesine ve tanımlanan uygulama düzeyi kaynaklarına devam eder.  
  
 [!code-xaml[ResourcesApplication#ConsumingPage](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/page1.xaml#consumingpage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML Kaynakları](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Uygulama Yönetimine Genel Bakış](../app-development/application-management-overview.md)
- [Nasıl Yapılır Konuları](resources-how-to-topics.md)
