---
title: "WCF Güvenliğinde Şifreleme Çevikliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 8b07b23f4428053964fa33150c4300645242f918
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="cryptographic-agility-in-wcf-security"></a>WCF Güvenliğinde Şifreleme Çevikliği
Bu örnek, bir şifreleme Çevik uygulamasında sağlamak için bir standart/özel algoritması belirtmek üzere gösterilmiştir bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] istemci ve hizmet. Örnek aşağıdaki projeleri oluşur:  
  
 Hizmet  
 Kendini barındıran budur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulayan hizmet `ICalculator` arabirim ve kullanarak uç nokta güvenliğini sağlama <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> güvenli oturum ve güvenilir oturum devre dışı. Özel bir hizmet tanımlar `SecurityAlgorithmSuite` ileti güvenliği için kullanılacak şifreleme algoritmalarını belirlemek için sınıf.  
  
 İstemci  
 Bu bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]başarılı kimlik doğrulamasından sonra hizmete erişen istemci. Tarafından sunulan işlemleri çağırır `ICalculator` arabirim ve hizmet tarafından uygulanır. İstemci Ayrıca aynı özel tanımlar `SecurityAlgorithmSuite` ileti güvenliği için kullanılacak şifreleme algoritmalarını belirlemek için sınıf.  
  
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
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenlik](../../../../docs/framework/wcf/feature-details/security.md)
