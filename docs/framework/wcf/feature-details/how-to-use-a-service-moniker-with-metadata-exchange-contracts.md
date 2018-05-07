---
title: 'Nasıl yapılır: Meta Veri Değişimi Sözleşmeleriyle Hizmet Bilinen Adı Kullanma'
ms.date: 03/30/2017
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
ms.openlocfilehash: 6265860c2e1efb2f74a0243157a223a33889629a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a>Nasıl yapılır: Meta Veri Değişimi Sözleşmeleriyle Hizmet Bilinen Adı Kullanma
Bazı yeni WCF hizmetleri geliştirme sonra bir komut dosyası veya Visual Basic 6.0 uygulamadan bu hizmetleri çağıran kullanabilmek ister karar verebilirsiniz. Bir yöntemin bir WCF istemcisi derlemesini oluşturmak, derlemesini COM ile kaydetme, derlemeyi GAC'ye yükleyin ve ardından Visual Basic kodunuzdan COM türlerini başvuru olacaktır. Uygulamayı dağıttığınızda, WCF istemcisi derleme de dağıtmak gerekecektir. Ardından, kullanıcı WCF istemcisi derlemesini COM ile kaydetme ve GAC'ye yerleştirmek sahip olur. WCF COM birlikte çalışma bir WCF istemcisi derlemeye bağlı olmadan aynı hizmeti çağrıları yapma sağlar. WCF bilinen adını herhangi bir WCF Hizmeti herhangi bir COM uyumlu dili (Visual Basic, VBScript, Visual Basic for Applications (VBA) ve benzeri) bir meta veri değişimi (Mex) uç noktası türü ayıklamak için hizmet adının kullanır URI belirterek çağırmanıza olanak tanır hizmeti hakkında bilgi. Bu konu, Mex uç nokta belirtir WCF bilinen adını kullanarak alma başlatıldı WCF örnek çağrı açıklar.  
  
> [!NOTE]
>  WCF istemci derlemesi tarafından tanımlanan türleri aslında hiç örneği. Derleme yalnızca meta veriler için kullanılır.  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a>Mex adresi ile hizmet bilinen adı kullanma  
  
1.  Başlarken örneği oluşturmak ve kendi URL'ye göz atmak için Internet Explorer kullanın (http://localhost/ServiceModelSamples/Service.svc) hizmetinin çalıştığından emin olmak için.  
  
2.  Visual Basic komut dosyası veya aşağıdaki kodu içeren bir Visual Basic uygulama oluşturun:  
  
    ```  
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3.  Visual Basic uygulama veya komut dosyasını çalıştırın.  
  
    > [!NOTE]
    >  Aradığınız hizmeti Mex bitiş noktası ad hizmeti meta verileri okuyabilir için kullanıma gerekir. Daha fazla bilgi için bkz: [nasıl yapılır: bir yapılandırma dosyası kullanarak bir hizmet için meta veri yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).  
  
    > [!NOTE]
    >  Ad hatalı veya hizmet kullanılamıyor çağrısı `GetObject` "Geçersiz sözdizimi." bildiren bir hata döndürür  Bu hatayı alırsanız, kullanmakta olduğunuz adının doğru olduğundan ve hizmet kullanılabilir olduğundan emin olun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Windows Communication Foundation Hizmeti Bilinen Adını Kaydolmadan Kullanma](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 [Nasıl yapılır: WSDL Sözleşmeleriyle Hizmet Bilinen Adı Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)
