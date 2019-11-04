---
title: 'Nasıl yapılır: Uygulama Kapsamı Kaynak Sözlüğü Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dictionaries [WPF], resource
- resource dictionaries [WPF], application-scope
- application-scope resource dictionaries
ms.assetid: 53857682-bd2c-4f2c-8f25-1307d0b451a2
ms.openlocfilehash: 5bfb3ed0304598a5acf4b7682bf4a4169c5153d1
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459801"
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a>Nasıl yapılır: Uygulama Kapsamı Kaynak Sözlüğü Kullanma
Bu örnek, uygulama kapsamı özel kaynak sözlüğünün nasıl tanımlanacağını ve kullanılacağını göstermektedir.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Application>, paylaşılan kaynaklar için uygulama kapsamı deposunu kullanıma sunar: <xref:System.Windows.Application.Resources%2A>. Varsayılan olarak, <xref:System.Windows.Application.Resources%2A> özelliği <xref:System.Windows.ResourceDictionary> türünün bir örneğiyle başlatılır. <xref:System.Windows.Application.Resources%2A>kullanarak uygulama kapsamı özelliklerini alırken ve ayarladığınızda bu örneği kullanırsınız. Daha fazla bilgi için bkz. [nasıl yapılır: uygulama kapsamı kaynağı alma ve ayarlama](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100)).
  
 <xref:System.Windows.Application.Resources%2A>kullanarak ayarladığınız birden fazla kaynağınız varsa, bunun yerine bu kaynakları depolamak için özel bir kaynak sözlüğü kullanabilir ve bunun yerine onunla <xref:System.Windows.Application.Resources%2A> ayarlayabilirsiniz. Aşağıda, XAML kullanarak özel bir kaynak sözlüğünün nasıl bildirildiği gösterilmektedir.
  
 [!code-xaml[HOWTOResourceDictionaries#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 <xref:System.Windows.Application.Resources%2A> kullanarak tüm kaynak sözlüklerinin takas işlemi, her temanın tek bir kaynak sözlüğü tarafından kapsüllendiği uygulama kapsamı temalarını desteketmenize olanak tanır. Aşağıdaki örnekte <xref:System.Windows.ResourceDictionary>nasıl ayarlanacağı gösterilmektedir.  
  
 [!code-xaml[HOWTOResourceDictionaries#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 Aşağıda, XAML 'de <xref:System.Windows.Application.Resources%2A> tarafından sunulan kaynak sözlüğünden uygulama kapsamı kaynaklarını nasıl alabileceğiniz gösterilmektedir.  
  
 [!code-xaml[HOWTOResourceDictionaries#4](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 Ayrıca, koddaki kaynakların nasıl alınacağını aşağıda görebilirsiniz.  
  
 [!code-csharp[HOWTOResourceDictionaries#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 <xref:System.Windows.Application.Resources%2A>kullanırken yapmanız gereken iki önemli noktalar vardır. İlk olarak, sözlük *anahtarı* bir nesnedir, bu nedenle her ikisi de bir özellik değeri ayarlarken ve alırken tam olarak aynı nesne örneğini kullanmanız gerekir. (Bir dize kullanılırken anahtarın büyük/küçük harfe duyarlı olduğunu unutmayın.) İkincisi, sözlük *değeri* bir nesnedir, bu nedenle bir özellik değeri alırken değeri istenen türe dönüştürmeniz gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.ResourceDictionary>
- <xref:System.Windows.Application.Resources%2A>
- [XAML Kaynakları](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Birleştirilmiş Kaynak Sözlükleri](../advanced/merged-resource-dictionaries.md)
