---
title: "Nasıl yapılır: Yerelleştirilebilir Uygulamalarda Kaynak Kullanımı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications [WPF], localizable
- localizable applications [WPF]
ms.assetid: 08539ad6-7fca-4f34-b82b-ff439e11dfa7
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e025b42a72def81420de7d82dcf027405669ce78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-resources-in-localizable-applications"></a>Nasıl yapılır: Yerelleştirilebilir Uygulamalarda Kaynak Kullanımı
Yerelleştirme anlamına gelir uyarlamak bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] farklı kültürler için. Metin gibi başlıklar, bunun için resim yazısı, liste kutusu öğeleri ve benzeri çevrilmesi gerekir. Çeviri kolaylaştırmak için çevrilecek öğeler kaynak dosyalarına toplanır. Bkz: [uygulama yerelleştirme](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md) yerelleştirme için kaynak dosyasının nasıl oluşturulacağı hakkında bilgi için. Yapmak için bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama yerelleştirilebilir, geliştiricilerin yerelleştirilebilir tüm kaynakları kaynak derlemesine derlemeleri gerekir. Kaynak assembly farklı dillere yerelleştirilmiştir ve kaynak yönetimi arka plan kodu kullanır [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] yüklenemiyor. İçin gereken dosyalardan biri bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir proje dosyası (.proj) uygulamasıdır. Uygulamanızı kullanan tüm kaynakları proje dosyasında bulunması gerekir. Aşağıdaki kod örneğinde bu gösterir.  
  
## <a name="example"></a>Örnek  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `<Resource Include="data\picture1.jpg"/>`  
  
 `<EmbeddedResource Include="data\stringtable.en-US.restext"/>`  
  
 Uygulamanıza bir kaynak kullanmak için örneği <xref:System.Resources.ResourceManager> ve kullanmak istediğiniz kaynağı yüklenemiyor. Bunun nasıl yapılacağı gösterilmektedir.  
  
 [!code-csharp[LocalizationResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]
