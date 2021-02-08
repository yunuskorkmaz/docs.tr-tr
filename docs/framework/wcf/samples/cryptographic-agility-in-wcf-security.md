---
description: 'Daha fazla bilgi edinin: WCF güvenliğine yönelik şifreleme çevikliği'
title: WCF güvenliğine ilişkin şifreleme çevikliği
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
ms.openlocfilehash: ab46034b16a846f7399220480fc928655d931be0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778353"
---
# <a name="cryptographic-agility-in-wcf-security"></a>WCF güvenliğine ilişkin şifreleme çevikliği

Bu örnek, bir Windows Communication Foundation (WCF) istemcisinde ve hizmetinde şifreli çevik uygulama sağlamak için standart/özel algoritmada nasıl belirtme gösterir. Örnek, aşağıdaki projelerden oluşur:

**Hizmet**

Bu, `ICalculator` arabirimini uygulayan ve <xref:System.ServiceModel.WSHttpBinding> güvenli oturum ve güvenilir oturumu devre dışı olarak kullanarak uç noktanın güvenliğini sağlayan, şirket içinde BARıNDıRıLAN bir WCF hizmetidir. Hizmet, `SecurityAlgorithmSuite` ileti güvenliği için kullanılacak şifreleme algoritmalarını belirtmek için özel bir sınıf tanımlar.

**İstemci**

Bu, başarılı kimlik doğrulamasından sonra hizmete erişen bir WCF istemcsahiptir. Arabirim tarafından sunulan `ICalculator` ve hizmet tarafından uygulanan işlemleri çağırır. İstemci Ayrıca, `SecurityAlgorithmSuite` ileti güvenliği için kullanılacak şifreleme algoritmalarını belirtmek için aynı özel sınıfı tanımlar.

## <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2012 ' de Cryptoçeviklik. sln çözümünü açın.

2. Çözümü derlemek için CTRL+SHIFT+B'ye basın.

3. Dosya Gezgini 'ni açın ve \WCF\Basic\Security\CryptoAgility\Service\bin dizinine gidin ve service.exe sağ tıklayıp **yönetici olarak çalıştır**' ı seçerek service.exe dosyasını yönetici ayrıcalıklarıyla çalıştırın.

4. \WCF\Basic\Security\CryptoAgility\Client\bin dizinine gidin ve client.exe dosyasını normal şekilde çalıştırın.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Communication Foundation Güvenliği](../feature-details/security.md)
