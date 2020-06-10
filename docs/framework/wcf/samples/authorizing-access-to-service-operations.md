---
title: Hizmet İşlemlerine Erişimi Yetkilendirme
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
ms.openlocfilehash: 3097c86f50a75dec8a649ca4e1edd2511a046ca8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585538"
---
# <a name="authorizing-access-to-service-operations"></a>Hizmet İşlemlerine Erişimi Yetkilendirme
Bu örnek, [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) <xref:System.Security.Permissions.PrincipalPermissionAttribute> hizmet işlemlerine erişim yetkisi vermek için özniteliğinin kullanımını etkinleştirmek üzere öğesinin nasıl kullanılacağını gösterir. Bu örnek, [kullanmaya](getting-started-sample.md) başlama örneğine dayalıdır. Hizmeti ve istemcisi kullanılarak yapılandırılır [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) . `mode`Öğesinin özniteliği [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) olarak ayarlanmıştır `Message` ve `clientCredentialType` olarak ayarlanmıştır `Windows` . <xref:System.Security.Permissions.PrincipalPermissionAttribute>Her bir hizmet yöntemine uygulanır ve her bir işleme erişimi kısıtlamak için kullanılır. Çağıranın her bir işleme erişmesi için bir Windows Yöneticisi olması gerekir.  
  
 Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Hizmet yapılandırma dosyası [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) özniteliğini ayarlamak için öğesini kullanır `principalPermissionMode` :  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior>
      <!-- The serviceAuthorization behavior sets the  
           principalPermissionMode to UseWindowsGroups.  
           This puts a WindowsPrincipal on the current thread when a   
           service is invoked. -->  
      <serviceAuthorization principalPermissionMode="UseWindowsGroups" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 İçin ayarı `principalPermissionMode` , `UseWindowsGroups` <xref:System.Security.Permissions.PrincipalPermissionAttribute> Windows Grup adlarına göre kullanımını sağlar.  
  
 , <xref:System.Security.Permissions.PrincipalPermissionAttribute> Aşağıdaki örnek kodda gösterildiği gibi çağıranın Windows yöneticileri grubunun bir parçası olmasını gerektirmek için her bir işleme uygulanır.  
  
```csharp
[PrincipalPermission(SecurityAction.Demand,
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemci, Yöneticiler grubunun parçası olan bir hesabın altında çalışıyorsa, her işlemle birlikte başarıyla iletişim kurar; Aksi takdirde, erişim reddedilir. Yetkilendirme hatasıyla denemeler yapmak için istemciyi Yöneticiler grubunun parçası olmayan bir hesap altında çalıştırın. İstemcisini kapatmak için konsol penceresinde ENTER tuşuna basın.  
  
 Bir hizmet, bir hizmeti uygulayarak yetkilendirme hatalarından haberdar olabilir <xref:System.ServiceModel.Dispatcher.IErrorHandler> . Uygulama hakkında bilgi için bkz. [hata işleme ve raporlama üzerinde denetimi genişletme](extending-control-over-error-handling-and-reporting.md) `IErrorHandler` .  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
