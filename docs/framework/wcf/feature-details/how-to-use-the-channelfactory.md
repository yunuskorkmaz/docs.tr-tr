---
title: 'Nasıl yapılır: ChannelFactory Kullanma'
description: WCF istemcisi kullanarak hizmetlere erişmek için birden fazla kanal oluşturmak üzere bir kanal fabrikası oluşturmayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
ms.openlocfilehash: 7c87026ca4cf7c739f4615da9bc7f0272a382392
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246668"
---
# <a name="how-to-use-the-channelfactory"></a>Nasıl yapılır: ChannelFactory Kullanma
Genel sınıf, birden <xref:System.ServiceModel.ChannelFactory%601> fazla kanal oluşturmak için kullanılabilecek bir kanal fabrikası oluşturulmasını gerektiren Gelişmiş senaryolarda kullanılır.  
  
### <a name="to-create-and-use-the-channelfactory-class"></a>ChannelFactory sınıfını oluşturmak ve kullanmak için  
  
1. Windows Communication Foundation (WCF) hizmetini derleyin ve çalıştırın. Daha fazla bilgi için bkz. [Hizmetleri tasarlama ve uygulama](../designing-and-implementing-services.md), [Hizmetleri yapılandırma](../configuring-services.md)ve [barındırma hizmetleri](../hosting-services.md).  
  
2. İstemci için sözleşme (arabirim) oluşturmak üzere [ServiceModel meta veri yardımcı programı aracını (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın.  
  
3. İstemci kodunda, <xref:System.ServiceModel.ChannelFactory%601> birden fazla uç nokta dinleyicisi oluşturmak için sınıfını kullanın.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
