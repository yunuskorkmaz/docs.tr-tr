---
title: "Nasıl yapılır: Uygulama Kapsamı Kaynak Sözlüğü Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dictionaries [WPF], resource
- resource dictionaries [WPF], application-scope
- application-scope resource dictionaries
ms.assetid: 53857682-bd2c-4f2c-8f25-1307d0b451a2
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 04dbcfb0fa16ceb4d6778ef611e926894d7840e9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a>Nasıl yapılır: Uygulama Kapsamı Kaynak Sözlüğü Kullanma
Bu örnek bir uygulama kapsamlı özel kaynak sözlüğü tanımlayın ve nasıl kullanılacağını gösterir.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Application>Paylaşılan kaynaklar için bir uygulama kapsamı deposu gösterir: <xref:System.Windows.Application.Resources%2A>. Varsayılan olarak, <xref:System.Windows.Application.Resources%2A> özelliği olan bir örneğine ilk <xref:System.Windows.ResourceDictionary> türü. Alma ve ayarlama kullanarak uygulama kapsamı özelliklerini olduğunda bu örneği kullanmak <xref:System.Windows.Application.Resources%2A>. Daha fazla bilgi için bkz: [nasıl yapılır: almak ve bir uygulama kapsamı kaynak ayarlamak](http://msdn.microsoft.com/library/39e0420c-c9fc-47dc-8956-fdd95b214095).
  
 Kullanılarak ayarlanan birden çok kaynaklarınız varsa <xref:System.Windows.Application.Resources%2A>, bunun yerine özel bir kaynak sözlüğü bu kaynakları depolamak ve ayarlamak için kullanabileceğiniz <xref:System.Windows.Application.Resources%2A> onunla yerine. XAML kullanarak özel bir kaynak sözlüğü bildirme nasıl gösterir.
  
 [!code-xaml[HOWTOResourceDictionaries#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 Tüm kaynak sözlüklerindeki kullanarak takas <xref:System.Windows.Application.Resources%2A> uygulama kapsamı temalarını desteklemek, burada her tema kapsüllenmiş tek bir kaynak sözlüğü tarafından sağlar. Aşağıdaki örnekte nasıl ayarlanacağını gösterir <xref:System.Windows.ResourceDictionary>.  
  
 [!code-xaml[HOWTOResourceDictionaries#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 Aşağıdaki tarafından gösterilen kaynak sözlüğünden uygulama kapsamı kaynaklarını nasıl erişebileceğini gösterir <xref:System.Windows.Application.Resources%2A> XAML'de.  
  
 [!code-xaml[HOWTOResourceDictionaries#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 Aşağıdaki nasıl Ayrıca kaynak kodunda alabileceğiniz gösterir.  
  
 [!code-csharp[HOWTOResourceDictionaries#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 Kullanırken yapmanız gereken iki noktalar vardır <xref:System.Windows.Application.Resources%2A>. İlk olarak, sözlük *anahtar* bir nesne olduğundan özellik değerini alırken ve tam olarak aynı nesne örneğini kullanmanız gerekir. (Bir dize kullanıldığında anahtarın büyük küçük harfe duyarlı olduğunu unutmayın.) İkincisi, sözlük *değeri* bir özellik değeri alırken değeri istenen türe çevirmeniz gerekir böylece bir nesnesidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.ResourceDictionary>  
 <xref:System.Windows.Application.Resources%2A>  
 [XAML Kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Birleştirilmiş Kaynak Sözlükleri](../../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md)
