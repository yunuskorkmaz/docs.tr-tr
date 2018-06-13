---
title: Hizmet İşlemlerine Erişimi Yetkilendirme
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
ms.openlocfilehash: b7f8b9b5fc4e6524da49b4d3f23de90a123e92e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33501487"
---
# <a name="authorizing-access-to-service-operations"></a>Hizmet İşlemlerine Erişimi Yetkilendirme
Bu örnek nasıl kullanılacağı ortaya [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) kullanımını etkinleştirmek için <xref:System.Security.Permissions.PrincipalPermissionAttribute> hizmet işlemlerine erişimi yetkilendirmek için öznitelik. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) örnek. İstemci ve hizmet kullanılarak yapılandırılmış olan [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). `mode` Özniteliği [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) ayarlandığından `Message` ve `clientCredentialType` ayarlandığından `Windows`. <xref:System.Security.Permissions.PrincipalPermissionAttribute> Her hizmet yöntemi uygulanır ve her işlem için erişimi kısıtlamak için kullanılır. Çağıran, her işlem erişmek için bir Windows yöneticisi olmanız gerekir.  
  
 Bu örnekte, istemci bir konsol uygulaması (.exe) ve Internet Information Services (IIS) tarafından barındırılan hizmetindeki.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Hizmet yapılandırma dosyası kullanan [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) ayarlamak için `principalPermissionMode` özniteliği:  
  
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
  
 Ayarı `principalPermissionMode` için `UseWindowsGroups` kullanmayı sağlayan <xref:System.Security.Permissions.PrincipalPermissionAttribute> Windows grup adlarını temel alarak.  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> Aşağıdaki örnek kodda gösterildiği gibi Windows administrators grubunun bir parçası olarak çağıran gerektirecek şekilde her bir işlemin uygulanır.  
  
```  
[PrincipalPermission(SecurityAction.Demand,   
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. Yöneticiler grubunun bir parçası olan bir hesabı altında çalışıyorsa, istemci başarıyla her işlemi ile iletişim kurar; Aksi takdirde, erişim reddedildi. Yetkilendirme hatası ile denemek için Administrators grubunun parçası olmayan bir hesap altında istemci çalıştırın. Konsol penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
 Bir hizmet uygulayarak yetkilendirme hatalarının bildirilebilir bir <xref:System.ServiceModel.Dispatcher.IErrorHandler>. Bkz: [genişletme denetim üzerinden hata işleme ve Raporlama](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) uygulama hakkında bilgi için `IErrorHandler`.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.
