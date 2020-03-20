---
title: Hizmet İşlemlerine Erişimi Yetkilendirme
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
ms.openlocfilehash: c2ad6977674666ef65df1ea4cfe58cfd4bff8b69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183920"
---
# <a name="authorizing-access-to-service-operations"></a>Hizmet İşlemlerine Erişimi Yetkilendirme
Bu örnek, hizmet işlemlerine <xref:System.Security.Permissions.PrincipalPermissionAttribute> [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) erişimi yetkilendirmek için özniteliğin kullanımını etkinleştirmek için serviceAuthorization>'nin nasıl kullanılacağını gösterir. Bu örnek [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) örneği dayanmaktadır. Hizmet ve istemci [ \<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)kullanılarak yapılandırılır. `mode` `Message` `clientCredentialType` `Windows` [Güvenlik>özniteliği ayarlandı ve '' \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) olarak ayarlandı. Her <xref:System.Security.Permissions.PrincipalPermissionAttribute> hizmet yöntemine uygulanır ve her işlemiçin erişimi kısıtlamak için kullanılır. Arayan her işlem erişmek için bir Windows yöneticisi olmalıdır.  
  
 Bu örnekte, istemci bir konsol uygulamasıdır (.exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Hizmet yapılandırma dosyası, özniteliği ayarlamak `principalPermissionMode` için [ \<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) kullanır:  
  
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
  
 Windows `principalPermissionMode` grup `UseWindowsGroups` adlarını <xref:System.Security.Permissions.PrincipalPermissionAttribute> temel alan kullanımını etkinleştirmek için ayarlama.  
  
 Aşağıdaki <xref:System.Security.Permissions.PrincipalPermissionAttribute> örnek kodda gösterildiği gibi, arayanın Windows yöneticileri grubunun bir parçası olmasını gerektiren her işlem uygulanır.  
  
```csharp
[PrincipalPermission(SecurityAction.Demand,
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemci, Yöneticiler grubunun bir parçası olan bir hesap altında çalışıyorsa, her işlemle başarılı bir şekilde iletişim kurar; aksi takdirde, erişim reddedilir. Yetkilendirme hatasıyla denemeler yapmak için istemciyi Yöneticiler grubunun parçası olmayan bir hesap altında çalıştırın. İstemciyi kapatmak için konsol penceresinde ENTER tuşuna basın.  
  
 Bir hizmet, bir <xref:System.ServiceModel.Dispatcher.IErrorHandler>. Uygulama hakkında bilgi için [Hata İşleme ve Raporlama Üzerinde Denetimi Genişletme'ye](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) `IErrorHandler`bakın.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya bilgisayar lar arası yapılandırmada çalıştırmak [için, Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
