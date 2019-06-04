---
title: WCF güvenliğinde şifreleme çevikliği
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
ms.openlocfilehash: b8e3b6dc62baf31901520d7f5edac0529e937016
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490945"
---
# <a name="cryptographic-agility-in-wcf-security"></a>WCF güvenliğinde şifreleme çevikliği

Bu örnek, bir Windows Communication Foundation (WCF) istemci ve hizmet şifreleme ve Çevik bir uygulama sağlamak için bir standart/özel algoritması belirtin gösterilmektedir. Örnek, aşağıdaki projelerin oluşur:

**Hizmet**

Bu uygulayan şirket içinde barındırılan bir WCF hizmeti, `ICalculator` arabirim ve uç noktayı kullanarak korur <xref:System.ServiceModel.WSHttpBinding> güvenli oturum ve güvenilir oturum devre dışı. Özel bir hizmet tanımlar `SecurityAlgorithmSuite` ileti güvenliği için kullanılacak şifreleme algoritmalarını belirlemek için sınıf.

**İstemci**

Başarılı kimlik doğrulamasından sonra hizmete erişen bir WCF istemcisi budur. Tarafından sunulan işlemleri çağırır `ICalculator` arabirim ve hizmet tarafından uygulanır. İstemci Ayrıca, aynı özel tanımlar `SecurityAlgorithmSuite` ileti güvenliği için kullanılacak şifreleme algoritmalarını belirlemek için sınıf.

## <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2012'de CryptoAgility.sln çözümü açın.

2. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.

3. Dosya Gezgini'ni açın ve \WCF\Basic\Security\CryptoAgility\Service\bin dizine gidin ve service.exe sağ tıklatıp seçerek service.exe dosyasını yönetici ayrıcalıklarıyla çalıştırın **yönetici olarak çalıştır**.

4. \WCF\Basic\Security\CryptoAgility\Client\bin dizine gidin ve normalde client.exe dosyasını çalıştırın.

> [!IMPORTANT]
> Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Communication Foundation güvenliği](../feature-details/security.md)
