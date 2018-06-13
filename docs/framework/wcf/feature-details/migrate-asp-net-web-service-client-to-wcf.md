---
title: "Nasıl yapılır: ASP.NET Web Hizmeti İstemci Kodunu Windows Communication Foundation'a Taşıma"
ms.date: 03/30/2017
ms.assetid: 2e0a22a7-e1d5-4718-8997-4319a7cd9027
ms.openlocfilehash: cb60f9cb2e8f35ee703b049eae9e3d99c1ec7d49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491136"
---
# <a name="how-to-migrate-aspnet-web-service-client-code-to-the-windows-communication-foundation"></a>Nasıl yapılır: ASP.NET Web Hizmeti İstemci Kodunu Windows Communication Foundation'a Taşıma
Aşağıdaki yordamda, ASP.NET Web hizmeti istemci kodunu WCF'ye taşıma için izlenmesi gereken genel adımlar açıklanmaktadır.  
  
## <a name="procedure"></a>Yordam  
  
#### <a name="to-migrate-aspnet-web-service-client-code-to-wcf"></a>WCF için ASP.NET Web hizmeti istemci kodunu geçirmek için  
  
1.  Kapsamlı bir emin testleri kümesini istemci için mevcut.  
  
2.  .NET 2.0 istemci uygulamaya yükseltmek için Visual Studio 2005 kullanın. Test kümesini çalıştırın.  
  
3.  ASP.NET istemci kodu istemci projeden kaldırın. Kod modülleri WSDL.exe aracı kullanılarak oluşturulan olduğunu.  
  
4.  WCF istemci kodu kullanarak Oluştur [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Bu kod istemci projenize ekleyin ve istemcinin var olan yapılandırma dosyasına yapılandırma çıktısını birleştirin.  
  
5.  Uygulamayı derleyin. Derleme hataları yeni WCF istemci türlerini başvuruları eski ASP.NET istemci tür başvuruları değiştirerek onarın.  
  
6.  Test kümesini çalıştırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: ASP.NET Web Hizmeti Kodunu Windows Communication Foundation'a Taşıma](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-to-wcf.md)
