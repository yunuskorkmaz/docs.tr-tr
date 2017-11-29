---
title: "Nasıl yapılır: ASP.NET Web Hizmeti İstemci Kodunu Windows Communication Foundation'a Taşıma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e0a22a7-e1d5-4718-8997-4319a7cd9027
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d77e07cca938b67f5b79416ac4d8fdef96739ed2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-migrate-aspnet-web-service-client-code-to-the-windows-communication-foundation"></a>Nasıl yapılır: ASP.NET Web Hizmeti İstemci Kodunu Windows Communication Foundation'a Taşıma
ASP.NET Web hizmeti istemci kodunu geçirmek için izlenmesi gereken genel adımlar aşağıdaki yordamda açıklanmıştır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="procedure"></a>Yordam  
  
#### <a name="to-migrate-aspnet-web-service-client-code-to-wcf"></a>WCF için ASP.NET Web hizmeti istemci kodunu geçirmek için  
  
1.  Kapsamlı bir emin testleri kümesini istemci için mevcut.  
  
2.  .NET 2.0 istemci uygulamaya yükseltmek için Visual Studio 2005 kullanın. Test kümesini çalıştırın.  
  
3.  ASP.NET istemci kodu istemci projeden kaldırın. Kod modülleri WSDL.exe aracı kullanılarak oluşturulan olduğunu.  
  
4.  Oluştur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci kodu kullanarak [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Bu kod istemci projenize ekleyin ve istemcinin var olan yapılandırma dosyasına yapılandırma çıktısını birleştirin.  
  
5.  Uygulamayı derleyin. Yeni başvuruları eski ASP.NET istemci tür başvuruları değiştirerek derleme hataları onarmak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci türü.  
  
6.  Test kümesini çalıştırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: ASP.NET Web hizmeti kodunu Windows Communication Foundation'a taşıma](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-to-wcf.md)
