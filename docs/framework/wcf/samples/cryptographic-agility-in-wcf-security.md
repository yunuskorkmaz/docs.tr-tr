---
title: WCF güvenliğinde şifreleme çevikliği
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
ms.openlocfilehash: 64519e51b82780ce2b355251245d77bff0a9e73b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62002215"
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

3. Açık [!INCLUDE[fileExplorer](~/includes/fileexplorer-md.md)] \WCF\Basic\Security\CryptoAgility\Service\bin dizine gidin ve service.exe sağ tıklatıp seçerek service.exe dosyasını yönetici ayrıcalıklarıyla çalıştırın **yönetici olarak çalıştır**.

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