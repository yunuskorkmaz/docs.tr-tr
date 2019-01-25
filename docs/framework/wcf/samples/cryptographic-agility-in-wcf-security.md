---
title: WCF Güvenliğinde Şifreleme Çevikliği
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
ms.openlocfilehash: a97f0b908d3c4d2e14fb55ec21371322dc740e47
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54668905"
---
# <a name="cryptographic-agility-in-wcf-security"></a>WCF Güvenliğinde Şifreleme Çevikliği
Bu örnek, bir Windows Communication Foundation (WCF) istemci ve hizmet şifreleme ve Çevik bir uygulama sağlamak için bir standart/özel algoritması belirtin gösterilmektedir. Örnek, aşağıdaki projelerin oluşur:

 Bu, uygulayan şirket içinde barındırılan bir WCF hizmeti hizmet `ICalculator` arabirim ve uç noktayı kullanarak güvenliğini sağlar <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> güvenli oturum ve güvenilir oturum devre dışı. Özel bir hizmet tanımlar `SecurityAlgorithmSuite` ileti güvenliği için kullanılacak şifreleme algoritmalarını belirlemek için sınıf.

 İstemci başarılı kimlik doğrulamasından sonra hizmete erişen bir WCFclient budur. Tarafından sunulan işlemleri çağırır `ICalculator` arabirim ve hizmet tarafından uygulanır. İstemci Ayrıca, aynı özel tanımlar `SecurityAlgorithmSuite` ileti güvenliği için kullanılacak şifreleme algoritmalarını belirlemek için sınıf.

### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1.  Visual Studio 2012'de CryptoAgility.sln çözümü açın.

2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.

3.  Açık [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] \WCF\Basic\Security\CryptoAgility\Service\bin dizine gidin ve service.exe sağ tıklatıp seçerek service.exe dosyasını yönetici ayrıcalıklarıyla çalıştırın **yönetici olarak çalıştır**.

4.  \WCF\Basic\Security\CryptoAgility\Client\bin dizine gidin ve normalde client.exe dosyasını çalıştırın.

> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Güvenlik](../../../../docs/framework/wcf/feature-details/security.md)
