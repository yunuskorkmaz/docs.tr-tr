---
title: "Model-Görünüm-Görünüm Model ile Taşınabilir Sınıf Kitaplığı Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Portable Class Library [.NET Framework], and MVVM
- MVVM, and Portable Class Library
ms.assetid: 41a0b9f8-15a2-431a-bc35-e310b2953b03
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: da1a05a6003d93727efd5749aac9a055c8c80d38
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="using-portable-class-library-with-model-view-view-model"></a>Model-Görünüm-Görünüm Model ile Taşınabilir Sınıf Kitaplığı Kullanma
.NET Framework kullanabilirsiniz [taşınabilir sınıf kitaplığı](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) Model-görünüm-görünüm Model (MVVM) desen uygulamak ve birden çok platform genelinde derlemeleri paylaşmak için.  
  
 MVVM temel iş mantığı kullanıcı arabiriminden yalıtan bir uygulama düzeni ' dir. Model ve görünüm modeli sınıflarda uygulayabileceğiniz bir [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] proje [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]ve ardından farklı platform için özelleştirilmiş görünümler oluşturabilirsiniz. Bu yaklaşım, veri yazmak sağlar modeli ve yalnızca bir kez iş mantığı ve .NET Framework, Silverlight, Windows Phone kod kullanımı ve [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aşağıdaki çizimde gösterildiği gibi uygulamalar.  
  
 ![Diyagram MVVM ile taşınabilir](../../../docs/standard/cross-platform/media/portablemvvmdiagram.png "PortableMVVMdiagram")  
  
 Bu konuda MVVM desen hakkında genel bilgi sağlamaz. Yalnızca nasıl kullanılacağı hakkında bilgi sağlar [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] MVVM uygulamak için. MVVM hakkında daha fazla bilgi için bkz: [MVVM Quickstart](http://go.microsoft.com/fwlink/?LinkId=234934).  
  
## <a name="classes-that-support-mvvm"></a>MVVM destekleyen sınıfları  
 Hedeflediğinizde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], Silverlight ya da için Windows Phone 7.5, [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] proje, aşağıdaki sınıflar MVVM desen uygulamak için kullanılabilir:  
  
-   <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType>sınıfı  
  
-   <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType>sınıfı  
  
-   <xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType>sınıfı  
  
-   <xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType>sınıfı  
  
-   <xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType>sınıfı  
  
-   <xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType>sınıfı  
  
-   <xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType>sınıfı  
  
-   <xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType>sınıfı  
  
-   <xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType>sınıfı  
  
-   <xref:System.Windows.Input.ICommand?displayProperty=nameWithType>sınıfı  
  
-   Tüm sınıflarda <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> ad alanı  
  
## <a name="implementing-mvvm"></a>MVVM uygulama  
 MVVM uygulamak için genellikle model ve görünüm modeli oluşturduğunuz bir [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] , çünkü proje bir [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] proje taşınabilir olmayan proje başvuruda bulunamaz. Model ve görünüm modeli ayrı projelerinde veya aynı projede olabilir. Ayrı projeler kullanırsanız, bir başvuru görünüm model projeden modeli projeye ekleyin.  
  
 Model derlemek ve model projeleri görüntüledikten sonra bu derlemelerde görünüm içeriyor uygulamasında başvuru. Görünüm yalnızca görünüm model ile etkileşime giren, görünüm modeli içeren derleme başvurusu yeterlidir.  
  
### <a name="model"></a>Model  
 Aşağıdaki örnek, içinde yer alan bir Basitleştirilmiş model sınıfı gösterir. bir [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projesi.  
  
 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]  
  
 Aşağıdaki örnek, doldurmak, almak ve verileri güncelleştirmek için basit bir yol gösterir. bir [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projesi. Gerçek bir uygulamada, bir Windows Communication Foundation (WCF) hizmeti gibi bir kaynaktan veri almak.  
  
 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]  
  
### <a name="view-model"></a>Görünüm modeli  
 Görünüm modelleri için temel sınıf sık MVVM deseni uygularken eklenir. Aşağıdaki örnek, bir taban sınıfı gösterir.  
  
 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]  
  
 Uygulaması <xref:System.Windows.Input.ICommand> arabirimi MVVM deseni sıkça kullanılır. Aşağıdaki örnek uygulaması gösterir <xref:System.Windows.Input.ICommand> arabirimi.  
  
 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]  
  
 Aşağıdaki örnekte bir basitleştirilmiş görünüm modeli gösterilmektedir.  
  
 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a>Görüntüle  
 Gelen bir [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] uygulama, [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulaması, Silverlight tabanlı bir uygulamanın veya Windows Phone 7.5 uygulama, başvuru modeli ve görünüm modeli projeleri içeren derleme.  Ardından Görünüm model ile etkileşime giren bir görünüm oluşturun. Aşağıdaki örnek alır ve görünüm modeli verileri güncelleştiren basitleştirilmiş bir Windows Presentation Foundation (WPF) uygulamasını gösterir. Silverlight, Windows Phone benzer görünümler oluşturabilir veya [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar.  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Taşınabilir Sınıf Kitaplığı](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)
