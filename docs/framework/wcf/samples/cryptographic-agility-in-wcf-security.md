---
title: WCF Güvenliğinde Şifreleme Çevikliği
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 40f4f8523d5286911216180846e94ec18e40da1c
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33810219"
---
# <a name="cryptographic-agility-in-wcf-security"></a>WCF Güvenliğinde Şifreleme Çevikliği
Bu örnek, bir şifreleme Çevik uygulamasında bir Windows Communication Foundation (WCF) istemci ve hizmet sağlamak için bir standart/özel algoritması belirtmek üzere gösterilmiştir. Örnek aşağıdaki projeleri oluşur:  
  
 Hizmet  
 Bu uygulayan bir kendi kendini barındıran WCF hizmetidir `ICalculator` arabirim ve kullanarak uç nokta güvenliğini sağlama <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> güvenli oturum ve güvenilir oturum devre dışı. Özel bir hizmet tanımlar `SecurityAlgorithmSuite` ileti güvenliği için kullanılacak şifreleme algoritmalarını belirlemek için sınıf.  
  
 İstemci  
 Başarılı kimlik doğrulamasından sonra hizmete erişen bir WCFclient budur. Tarafından sunulan işlemleri çağırır `ICalculator` arabirim ve hizmet tarafından uygulanır. İstemci Ayrıca aynı özel tanımlar `SecurityAlgorithmSuite` ileti güvenliği için kullanılacak şifreleme algoritmalarını belirlemek için sınıf.  
  
### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  CryptoAgility.sln çözümde açmak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Açık [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] \WCF\Basic\Security\CryptoAgility\Service\bin dizine gidin ve service.exe sağ tıklayıp seçerek service.exe dosyasını yönetici ayrıcalıklarıyla çalıştırın **yönetici olarak çalıştır**.  
  
4.  \WCF\Basic\Security\CryptoAgility\Client\bin dizinine gidin ve client.exe dosya normal olarak çalışır.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenlik](../../../../docs/framework/wcf/feature-details/security.md)
