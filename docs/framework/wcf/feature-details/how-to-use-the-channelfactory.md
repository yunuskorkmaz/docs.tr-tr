---
title: "Nasıl yapılır: ChannelFactory Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 37ad5181ad140c3ef3ea8ba5b3774fd44310dca7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-the-channelfactory"></a>Nasıl yapılır: ChannelFactory Kullanma
Genel <xref:System.ServiceModel.ChannelFactory%601> sınıfı, birden fazla kanalı oluşturmak için kullanılan bir kanal fabrikası oluşturma gerektiren gelişmiş senaryolarda kullanılır.  
  
### <a name="to-create-and-use-the-channelfactory-class"></a>Oluşturma ve ChannelFactory sınıfı kullanma  
  
1.  Derleme ve çalıştırma bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmet. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Hizmetleri Tasarlama ve uygulama](../../../../docs/framework/wcf/designing-and-implementing-services.md), [Hizmetleri Yapılandırma](../../../../docs/framework/wcf/configuring-services.md), ve [barındırma hizmetleri](../../../../docs/framework/wcf/hosting-services.md).  
  
2.  Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) sözleşmenin (arabirimi) istemcisi oluşturmak için.  
  
3.  İstemci kodu kullanmak <xref:System.ServiceModel.ChannelFactory%601> birden çok uç nokta dinleyicileri oluşturmasını sağlar.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
