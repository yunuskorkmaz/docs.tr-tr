---
title: WCF güvenliğine ilişkin şifreleme çevikliği
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
ms.openlocfilehash: 2dbacd53876ded76ea212dd5656cd2dded4a6e48
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714932"
---
# <a name="cryptographic-agility-in-wcf-security"></a>WCF güvenliğine ilişkin şifreleme çevikliği

Bu örnek, bir Windows Communication Foundation (WCF) istemcisinde ve hizmetinde şifreli çevik uygulama sağlamak için standart/özel algoritmada nasıl belirtme gösterir. Örnek, aşağıdaki projelerden oluşur:

**Hizmet**

Bu, `ICalculator` arabirimini uygulayan ve güvenli oturum ve güvenilir oturum devre dışı bırakılmış <xref:System.ServiceModel.WSHttpBinding> kullanarak uç noktanın güvenliğini sağlayan, şirket içinde barındırılan bir WCF hizmetidir. Hizmet, ileti güvenliği için kullanılacak şifreleme algoritmalarını belirtmek için özel bir `SecurityAlgorithmSuite` sınıfını tanımlar.

**İstemci**

Bu, başarılı kimlik doğrulamasından sonra hizmete erişen bir WCF istemcsahiptir. `ICalculator` arabirimi tarafından sunulan ve hizmet tarafından uygulanan işlemleri çağırır. İstemci Ayrıca, ileti güvenliği için kullanılacak şifreleme algoritmalarını belirtmek için aynı özel `SecurityAlgorithmSuite` sınıfını tanımlar.

## <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2012 ' de Cryptoçeviklik. sln çözümünü açın.

2. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.

3. Dosya Gezgini 'ni açın ve \WCF\Basic\Security\CryptoAgility\Service\bin dizinine gidin ve Service. exe dosyasını sağ tıklayıp yönetici **olarak çalıştır**' ı seçerek yönetici ayrıcalıklarıyla çalıştırın.

4. \WCF\Basic\Security\CryptoAgility\Client\bin dizinine gidin ve Client. exe dosyasını normal olarak çalıştırın.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Communication Foundation güvenliği](../feature-details/security.md)
