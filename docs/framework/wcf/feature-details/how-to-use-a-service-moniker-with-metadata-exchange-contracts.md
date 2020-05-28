---
title: 'Nasıl yapılır: Meta Veri Değişimi Sözleşmeleriyle Hizmet Bilinen Adı Kullanma'
ms.date: 03/30/2017
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
ms.openlocfilehash: 8894fdc4fd085b9d55a8fc25043e5258c306024c
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84143484"
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a>Nasıl yapılır: Meta Veri Değişimi Sözleşmeleriyle Hizmet Bilinen Adı Kullanma
Bazı yeni WCF Hizmetleri geliştirdikten sonra, bu hizmetleri bir betikten veya Visual Basic 6,0 uygulamasından çağırabilmek istediğinize karar verebilirsiniz. Bir yöntem, bir WCF istemci derlemesi oluşturmak, derlemeyi COM 'a kaydetmek, derlemeyi GAC 'ye yüklemek ve ardından Visual Basic kodunuzda COM türlerine başvurmak olacaktır. Uygulamayı dağıttığınızda, WCF Istemci derlemesini de dağıtmanız gerekir. Daha sonra kullanıcının WCF istemci derlemesini COM 'a kaydetmesi ve GAC 'ye yerleştirmesini gerekecektir. WCF COM birlikte çalışması Ayrıca bir WCF istemci derlemesine bağlı olmadan aynı hizmet çağrılarını yapmanıza olanak sağlar. WCF takma adı, hizmet adının hizmet hakkındaki tür bilgilerini ayıklamak için kullandığı bir meta veri değişimi (MEX) uç noktası URI 'SI belirterek herhangi bir COM uyumlu dilden (Visual Basic, VBScript, Visual Basic for Applications (VBA) vb.) herhangi bir WCF hizmetini çağırmanızı sağlar. Bu konu, bir MEX uç noktası belirten bir WCF bilinen adı kullanılarak Başlarken WCF örneğinin nasıl çağrılacağını açıklar.  
  
> [!NOTE]
> WCF istemci derlemesi tarafından tanımlanan türler aslında örneklenemez. Derleme yalnızca meta veriler için kullanılır.  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a>Hizmet bilinen adını bir Mex adresiyle kullanma  
  
1. Hizmetin çalıştığından emin olmak için başlangıç örneğini oluşturun ve URL 'sine () gitmek için Internet Explorer 'ı kullanın `http://localhost/ServiceModelSamples/Service.svc` .  
  
2. Aşağıdaki kodu içeren bir Visual Basic betiği veya Visual Basic uygulaması oluşturun:  
  
    ```vb
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3. Visual Basic uygulamayı veya betiği çalıştırın.  
  
    > [!NOTE]
    > Çağırmak için kullandığınız hizmet, bilinen adın meta verileri hizmetten okuyabilmesi için bir MEX uç noktası kullanıma sunmalıdır. Daha fazla bilgi için bkz. [nasıl yapılır: yapılandırma dosyası kullanarak bir hizmet Için meta verileri yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).  
  
    > [!NOTE]
    > Bilinen ad yanlış biçimlendirilmişse veya hizmet kullanılamıyorsa, çağrısı `GetObject` "geçersiz sözdizimi" belirten bir hata döndürür.  Bu hatayı alırsanız, kullanmakta olduğunuz bilinen adın doğru olduğundan ve hizmetin kullanılabilir olduğundan emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Windows Communication Foundation Hizmeti Bilinen Adını Kaydolmadan Kullanma](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)
- [Nasıl yapılır: WSDL Sözleşmeleriyle Hizmet Bilinen Adı Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)
