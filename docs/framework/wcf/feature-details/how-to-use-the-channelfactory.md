---
title: 'Nasıl yapılır: ChannelFactory Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
ms.openlocfilehash: 7d542a3dcae514e75194b49c23a8dec5dd7e8c3b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59298857"
---
# <a name="how-to-use-the-channelfactory"></a>Nasıl yapılır: ChannelFactory Kullanma
Genel <xref:System.ServiceModel.ChannelFactory%601> sınıfı, birden fazla kanal oluşturmak için kullanılan kanal fabrikası oluşturulmasını gerektiren gelişmiş senaryolarda kullanılır.  
  
### <a name="to-create-and-use-the-channelfactory-class"></a>Oluşturma ve kullanma ChannelFactory sınıfı  
  
1. Oluşturun ve bir Windows Communication Foundation (WCF) hizmetini çalıştırın. Daha fazla bilgi için [Hizmetleri Tasarlama ve uygulama](../../../../docs/framework/wcf/designing-and-implementing-services.md), [Hizmetleri'ni Yapılandırma](../../../../docs/framework/wcf/configuring-services.md), ve [barındırma hizmetleri](../../../../docs/framework/wcf/hosting-services.md).  
  
2. Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) istemci için anlaşma (arabirimi) oluşturmak için.  
  
3. İstemci kodunuzda kullanabileceğiniz <xref:System.ServiceModel.ChannelFactory%601> birden fazla uç noktası dinleyicisi oluşturmak için sınıf.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
