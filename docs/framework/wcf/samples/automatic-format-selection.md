---
title: "Otomatik Biçim Seçimi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dab51e56-8517-4a6a-bb54-b55b15ab37bb
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da09df968bffee9a07f1c03d5b771271a9d44129
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="automatic-format-selection"></a>Otomatik Biçim Seçimi
Bu örnek Otomatik Biçim Seçimi (XML veya JSON) etkinleştirmek ile gösterilmiştir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] REST programlama modeli yanı sıra biçim işlemi kodda açıkça ayarlamak üzere nasıl.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Örnek hizmete istek yaptığında istemci kodu ile birlikte bir servis oluşur. Tek bir HTTP hizmeti destekler `GET` işlemi (`EchoWithGet`) ve tek bir HTTP `POST` işlemi (`EchoWithPost`). İki işlem bir dize beklediğiniz ve sonra yanıtta dize döndürür. İle `GET` işlemi, dize URI sorgu dizesi parametresi sağlanır. İle `POST` işlemi, dize XML serileştirilmiş istek gövdesinde sağlanır. Hizmet XML veya JSON, kesinlik temelli Biçim Seçimi özellikleri ve yeni Otomatik Biçim Seçimi kullanılarak yanıtları döndürün yapabiliyor [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].  
  
 Aşağıdaki örnekte, App.config dosyası kullanarak Otomatik Biçim Seçimi etkinleştirilir. Varsayılan Web HTTP uç `automaticFormatSelectionEnabled` öznitelik değerini verildiği `true`. Etkin, otomatik biçim seçimi ile [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] altyapı isteğin HTTP kabul edin veya Content-Type üstbilgisi verilen en uygun yanıt biçimi (XML veya JSON) seçer. Geliştirici herhangi bir ek kod veya yapılandırma ayarı dışında sağlamak için gerekli olmayan `automaticFormatSelectionEnabled` özniteliğini `true` yeni bu özelliği kullanmak için. Program.cs istemci kodda iki gönderdiği istekleri `GET` ve `POST` "application/xml" veya "application/json" olarak belirtilen HTTP kabul başlık hizmetiyle ve hizmet işlemleri, bir yanıt döndürür ilgili biçimi.  
  
 Ayrıca, `GET` işlemi, kesinlik temelli Biçim Seçimi kullanılır. `GET` İşlemi için bir isteğe bağlı denetimlerini `format` sorgu dizesi parametresi ve varsa, yanıt biçimi ayarlar <xref:System.ServiceModel.Web.WebOperationContext.OutgoingResponse%2A> özelliği. Yanıt biçimi bu şekilde imperatively ayarını geçersiz kılar gerçekleştirilir Otomatik Biçim Seçimi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] altyapı.  
  
 Kendini barındıran hizmet ve bir konsol uygulaması içinde çalıştırılan bir istemciyi, örnek oluşur. Konsol uygulaması çalışırken, istemci hizmete istek yaptığında ve konsol penceresine yanıtlardan bilgileri yazar.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Çözümü için Otomatik Biçim Seçimi örneği açın. Başlatılırken [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], başarılı bir şekilde çalıştırmak için örnek yönetici olarak çalıştırmanız gerekir. Sağ tıklayarak bunu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] simgesi ve select **yönetici olarak çalıştır** ve bağlam menüsünden.  
  
2.  Çözümü derlemek ve konsol uygulaması AutomaticFormatSelection projesini çalıştırmak için Ctrl + F5 tuşuna basın CTRL + SHIFT + B tuşuna basın. Konsol penceresinde görüntülenir ve çalışan hizmetin URI sağlar ve URI HTML sayfası çalışan hizmetin için yardımcı olur.  
  
3.  Örnek çalışırken, istemci istekleri hizmetine gönderir ve yanıtları konsol penceresine yazar. XML ve JSON yanıtların farklı biçimleri dikkat edin.  
  
4.  Örnek sonlandırmak için herhangi bir tuşa basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AutomaticFormatSelection`  
  
## <a name="see-also"></a>Ayrıca Bkz.
