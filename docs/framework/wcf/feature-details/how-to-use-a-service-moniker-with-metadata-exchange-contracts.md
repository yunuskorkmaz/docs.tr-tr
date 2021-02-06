---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: meta veri değişimi sözleşmeleriyle hizmet bilinen adı kullanma'
title: 'Nasıl yapılır: Meta Veri Değişimi Sözleşmeleriyle Hizmet Bilinen Adı Kullanma'
ms.date: 03/30/2017
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
ms.openlocfilehash: 220132a10cb637be9e3724232d0ddaf80a13551a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643104"
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
    > Çağırmak için kullandığınız hizmet, bilinen adın meta verileri hizmetten okuyabilmesi için bir MEX uç noktası kullanıma sunmalıdır. Daha fazla bilgi için bkz. [nasıl yapılır: yapılandırma dosyası kullanarak bir hizmet Için meta verileri yayımlama](how-to-publish-metadata-for-a-service-using-a-configuration-file.md).  
  
    > [!NOTE]
    > Bilinen ad yanlış biçimlendirilmişse veya hizmet kullanılamıyorsa, çağrısı `GetObject` "geçersiz sözdizimi" belirten bir hata döndürür.  Bu hatayı alırsanız, kullanmakta olduğunuz bilinen adın doğru olduğundan ve hizmetin kullanılabilir olduğundan emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Windows Communication Foundation Hizmeti Bilinen Adını Kaydolmadan Kullanma](use-the-wcf-service-moniker-without-registration.md)
- [Nasıl yapılır: WSDL Sözleşmeleriyle Hizmet Bilinen Adı Kullanma](how-to-use-a-service-moniker-with-wsdl-contracts.md)
