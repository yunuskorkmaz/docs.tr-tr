---
title: Hizmet İşlemlerine Erişimi Yetkilendirme
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
ms.openlocfilehash: a0ea82c876b3bd8c2a3218f84399fbb69e1d0080
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932505"
---
# <a name="authorizing-access-to-service-operations"></a>Hizmet İşlemlerine Erişimi Yetkilendirme
Bu örnek, <xref:System.Security.Permissions.PrincipalPermissionAttribute> [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) hizmet işlemlerine erişim yetkisi vermek için özniteliğinin kullanımını etkinleştirmek üzere ServiceAuthorization > nasıl kullanacağınızı gösterir. Bu örnek, [kullanmaya](../../../../docs/framework/wcf/samples/getting-started-sample.md) başlama örneğine dayalıdır. Hizmet ve istemci, [ \<WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)kullanılarak yapılandırılır. `mode` Güvenlik>`Message` özniteliği olarakayarlanmıştır`clientCredentialType` ve olarak ayarlanmıştır.`Windows` [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) <xref:System.Security.Permissions.PrincipalPermissionAttribute> Her bir hizmet yöntemine uygulanır ve her bir işleme erişimi kısıtlamak için kullanılır. Çağıranın her bir işleme erişmesi için bir Windows Yöneticisi olması gerekir.  
  
 Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Hizmet yapılandırma dosyası, `principalPermissionMode` özelliği ayarlamak için [ \<ServiceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) kullanır:  
  
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
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> İçin `principalPermissionMode` ayarı`UseWindowsGroups` , Windows Grup adlarına göre kullanımını sağlar.  
  
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
  
 Bir hizmet, bir <xref:System.ServiceModel.Dispatcher.IErrorHandler>hizmeti uygulayarak yetkilendirme hatalarından haberdar olabilir. Uygulama`IErrorHandler`hakkında bilgi Için bkz. [hata Işleme ve raporlama üzerinde denetimi genişletme](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) .  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
