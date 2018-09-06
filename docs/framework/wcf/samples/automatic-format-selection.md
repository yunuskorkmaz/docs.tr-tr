---
title: Otomatik Biçim Seçimi
ms.date: 03/30/2017
ms.assetid: dab51e56-8517-4a6a-bb54-b55b15ab37bb
ms.openlocfilehash: 4fd695195f5c7c13bc088248a6b3c12388328d37
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43784764"
---
# <a name="automatic-format-selection"></a>Otomatik Biçim Seçimi
Bu örnek, biçimini işlemi kodda açıkça ayarlamak nasıl yanı sıra model programlama Windows Communication Foundation (WCF) REST ile otomatik biçim seçimi (XML veya JSON) etkinleştirme gösterir.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Bir hizmet için hizmet isteği yapan istemci kodunun yanı sıra örnek oluşur. Tek bir HTTP hizmetinin desteklediği `GET` işlemi (`EchoWithGet`) ve tek bir HTTP `POST` işlemi (`EchoWithPost`). Her iki işlem beklediğiniz bir dize ve dize yanıtta dönün. İle `GET` işlemi, dize bir URI sorgu dizesi parametresi sağlanır. İle `POST` işlemi, dize XML olarak serileştirilme istek gövdesinde sağlanır. Hizmet, XML veya JSON, kesinlik temelli Biçim Seçimi özellikleri ve yeni Otomatik Biçim Seçimi yararlanarak yanıtlarını döndürmek bulabildiği [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].  
  
 Bu örnekte App.config dosyasını kullanarak Otomatik Biçim Seçimi etkinleştirilir. Varsayılan Web HTTP uç noktasında `automaticFormatSelectionEnabled` öznitelik değerini verildiği `true`. Etkin otomatik biçim seçimi ile WCF altyapısı verilen İstek HTTP kabul edin veya Content-Type üstbilgisi en uygun yanıt biçimi (XML veya JSON) seçer. Geliştirici herhangi bir ek kod veya yapılandırma ayarı dışında sağlamak için gerekli olmayan `automaticFormatSelectionEnabled` özniteliğini `true` bu yeni özelliği kullanmak için. İstemci program.cs'deki kodu her iki gönderdiği istekleri `GET` ve `POST` "application/xml" veya "application/json" olarak belirtilen HTTP kabul başlık hizmetiyle ve hizmet işlemleri, bir yanıt döndürür ilgili biçimi.  
  
 Ayrıca `GET` işlemi, kesinlik temelli Biçim Seçimi kullanılır. `GET` İşlemi için bir isteğe bağlı denetler `format` sorgu dizesi parametresi ve yanıt biçimi varsa, ayarlar <xref:System.ServiceModel.Web.WebOperationContext.OutgoingResponse%2A> özelliği. Kesin yanıt biçimi bu şekilde ayarlama, WCF altyapısı tarafından yapılan otomatik biçim seçimi geçersiz kılar.  
  
 Örnek şirket içinde barındırılan bir hizmet ve içinde bir konsol uygulaması çalıştıran bir istemciyi oluşur. Konsol uygulamasının çalışır gibi istemci hizmete isteği yapan ve konsol penceresine yanıtlardan bilgileri yazar.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Otomatik Biçim Seçimi örneği için çözümü açın. Başlatma sırasında [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], başarılı bir şekilde yürütmek için örnek için yönetici çalıştırmanız gerekir. Sağ tıklayarak bunu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] simgesini seçip alt **yönetici olarak çalıştır** bağlam menüsünden.  
  
2.  Çözümü derleyin ve konsol uygulaması AutomaticFormatSelection projeyi çalıştırmak için Ctrl + F5 tuşuna basın CTRL + SHIFT + B tuşlarına basın. Konsol penceresinde görünür ve çalışan hizmetin URI sağlar ve URI HTML Yardım sayfası çalışan hizmeti.  
  
3.  Örnek çalışırken, istemci hizmete istekler gönderir ve konsol penceresine yanıtları yazar. XML ve JSON yanıtların farklı biçimler dikkat edin.  
  
4.  Örnek sonlandırmak için herhangi bir tuşa basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AutomaticFormatSelection`  
  
## <a name="see-also"></a>Ayrıca Bkz.
