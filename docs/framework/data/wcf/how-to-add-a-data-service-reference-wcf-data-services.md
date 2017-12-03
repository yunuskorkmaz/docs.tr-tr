---
title: "Nasıl yapılır: bir veri hizmeti başvurusu (WCF Veri Hizmetleri) Ekle"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 702eda2d4641dc2efdac40f9d730228063e306a8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a>Nasıl yapılır: bir veri hizmeti başvurusu (WCF Veri Hizmetleri) Ekle
Kullanabileceğiniz **hizmet Başvurusu Ekle** iletişim için bir başvuru eklemek için Visual Studio'da [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Bu, Visual Studio geliştirme istemci uygulamasında veri hizmeti daha kolay erişmesini sağlar. Bu yordamı tamamladıktan sonra veri sınıfları veri hizmetinden alınan meta veri göre oluşturulur. Daha fazla bilgi için bkz: [veri hizmeti istemci kitaplığı oluşturma](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).  
  
### <a name="to-add-a-data-service-reference"></a>Veri hizmeti başvurusu eklemek için  
  
1.  (İsteğe bağlı) Veri Hizmeti çözümün bir parçası değil ve çalışır durumda değil, veri hizmeti başlatın ve veri hizmeti URI'sini unutmayın.  
  
2.  İstemci projesine sağ tıklayın ve ardından **hizmet Başvurusu Ekle**.  
  
3.  Veri Hizmeti geçerli çözümün bir parçası ise, tıklatın **bulma**.  
  
     veya  
  
     İçinde **adresi** metin kutusuna, veri hizmeti temel URL'sini yazın gibi `http://localhost:1234/Northwind.svc`ve ardından **Git**.  
  
4.  **Tamam**'ı tıklatın.  
  
     Bu, erişim ve nesneler olarak veri hizmeti kaynakları ile etkileşim kurmak için kullanılan veri sınıfları içeren yeni bir kod dosyası ekler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
