---
title: 'Nasıl yapılır: ChannelFactory Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
ms.openlocfilehash: 4bb2053fb50931756e79d5346a3f14d2acbe04f6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595316"
---
# <a name="how-to-use-the-channelfactory"></a>Nasıl yapılır: ChannelFactory Kullanma
Genel sınıf, birden <xref:System.ServiceModel.ChannelFactory%601> fazla kanal oluşturmak için kullanılabilecek bir kanal fabrikası oluşturulmasını gerektiren Gelişmiş senaryolarda kullanılır.  
  
### <a name="to-create-and-use-the-channelfactory-class"></a>ChannelFactory sınıfını oluşturmak ve kullanmak için  
  
1. Windows Communication Foundation (WCF) hizmetini derleyin ve çalıştırın. Daha fazla bilgi için bkz. [Hizmetleri tasarlama ve uygulama](../designing-and-implementing-services.md), [Hizmetleri yapılandırma](../configuring-services.md)ve [barındırma hizmetleri](../hosting-services.md).  
  
2. İstemci için sözleşme (arabirim) oluşturmak üzere [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın.  
  
3. İstemci kodunda, <xref:System.ServiceModel.ChannelFactory%601> birden fazla uç nokta dinleyicisi oluşturmak için sınıfını kullanın.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
