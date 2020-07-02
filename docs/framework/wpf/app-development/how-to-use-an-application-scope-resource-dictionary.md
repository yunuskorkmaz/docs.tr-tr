---
title: 'Nasıl yapılır: Uygulama Kapsamı Kaynak Sözlüğü Kullanma'
description: Windows Presentation Foundation (WPF) içinde uygulama kapsamı özel kaynak sözlüğünü tanımlama ve kullanma hakkında bilgi edinin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dictionaries [WPF], resource
- resource dictionaries [WPF], application-scope
- application-scope resource dictionaries
ms.assetid: 53857682-bd2c-4f2c-8f25-1307d0b451a2
ms.openlocfilehash: 9d117dea6c554339b4b462b9bf37b80da2dc477f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85613715"
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a>Nasıl yapılır: Uygulama Kapsamı Kaynak Sözlüğü Kullanma
Bu örnek, uygulama kapsamı özel kaynak sözlüğünün nasıl tanımlanacağını ve kullanılacağını göstermektedir.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Application>paylaşılan kaynaklar için uygulama kapsamı deposu sunar: <xref:System.Windows.Application.Resources%2A> . Varsayılan olarak, <xref:System.Windows.Application.Resources%2A> özelliği türünün bir örneğiyle başlatılır <xref:System.Windows.ResourceDictionary> . Kullanarak uygulama kapsamı özelliklerini alırken ve ayarladığınızda bu örneği kullanırsınız <xref:System.Windows.Application.Resources%2A> . Daha fazla bilgi için bkz. [nasıl yapılır: uygulama kapsamı kaynağı alma ve ayarlama](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100)).
  
 Kullanarak ayarladığınız birden fazla kaynağınız varsa <xref:System.Windows.Application.Resources%2A> , bunun yerine bu kaynakları depolamak ve ile ayarlamak için özel bir kaynak sözlüğü kullanabilirsiniz <xref:System.Windows.Application.Resources%2A> . Aşağıda, XAML kullanarak özel bir kaynak sözlüğünün nasıl bildirildiği gösterilmektedir.
  
 [!code-xaml[HOWTOResourceDictionaries#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 Kullanarak tüm kaynak sözlüklerinin takas <xref:System.Windows.Application.Resources%2A> işlemi, her temanın tek bir kaynak sözlüğü tarafından kapsüllendiği uygulama kapsamı temalarını desteketmenize olanak tanır. Aşağıdaki örnekte, nasıl ayarlanacağı gösterilmektedir <xref:System.Windows.ResourceDictionary> .  
  
 [!code-xaml[HOWTOResourceDictionaries#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 Aşağıda, XAML 'de tarafından sunulan kaynak sözlüğünden uygulama kapsamı kaynaklarını nasıl alabileceğiniz gösterilmektedir <xref:System.Windows.Application.Resources%2A> .  
  
 [!code-xaml[HOWTOResourceDictionaries#4](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 Ayrıca, koddaki kaynakların nasıl alınacağını aşağıda görebilirsiniz.  
  
 [!code-csharp[HOWTOResourceDictionaries#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 Kullanırken yapmanız gereken iki önemli noktalar vardır <xref:System.Windows.Application.Resources%2A> . İlk olarak, sözlük *anahtarı* bir nesnedir, bu nedenle her ikisi de bir özellik değeri ayarlarken ve alırken tam olarak aynı nesne örneğini kullanmanız gerekir. (Bir dize kullanılırken anahtarın büyük/küçük harfe duyarlı olduğunu unutmayın.) İkincisi, sözlük *değeri* bir nesnedir, bu nedenle bir özellik değeri alırken değeri istenen türe dönüştürmeniz gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.ResourceDictionary>
- <xref:System.Windows.Application.Resources%2A>
- [XAML Kaynakları](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Birleştirilmiş Kaynak Sözlükleri](../advanced/merged-resource-dictionaries.md)
