---
title: WCF Güvenliğinde Şifreleme Çevikliği
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
author: BrucePerlerMS
ms.openlocfilehash: df40a87e2fe58b93a963d53fc79f88bbc7bdb805
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47171627"
---
# <a name="cryptographic-agility-in-wcf-security"></a>WCF Güvenliğinde Şifreleme Çevikliği
Bu örnek, bir Windows Communication Foundation (WCF) istemci ve hizmet şifreleme ve Çevik bir uygulama sağlamak için bir standart/özel algoritması belirtin gösterilmektedir. Örnek, aşağıdaki projelerin oluşur:  
  
 Hizmet  
 Bu uygulayan şirket içinde barındırılan bir WCF hizmeti, `ICalculator` arabirim ve uç noktayı kullanarak güvenliğini sağlar <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> güvenli oturum ve güvenilir oturum devre dışı. Özel bir hizmet tanımlar `SecurityAlgorithmSuite` ileti güvenliği için kullanılacak şifreleme algoritmalarını belirlemek için sınıf.  
  
 İstemci  
 Başarılı kimlik doğrulamasından sonra hizmete erişen bir WCFclient budur. Tarafından sunulan işlemleri çağırır `ICalculator` arabirim ve hizmet tarafından uygulanır. İstemci Ayrıca, aynı özel tanımlar `SecurityAlgorithmSuite` ileti güvenliği için kullanılacak şifreleme algoritmalarını belirlemek için sınıf.  
  
### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  CryptoAgility.sln çözümde açık [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenlik](../../../../docs/framework/wcf/feature-details/security.md)
