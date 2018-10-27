---
title: Hizmet İşlemlerine Erişimi Yetkilendirme
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
ms.openlocfilehash: 17148f9f1f8f197963ea97f18548d7e2f0826a8a
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50182118"
---
# <a name="authorizing-access-to-service-operations"></a>Hizmet İşlemlerine Erişimi Yetkilendirme
Bu örnek nasıl kullanılacağını gösterir [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) kullanımını etkinleştirmek için <xref:System.Security.Permissions.PrincipalPermissionAttribute> hizmet işlemleri erişim yetkisi vermek için özniteliği. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) örnek. Hizmet ve istemci kullanarak yapılandırılan [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). `mode` Özniteliği [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) ayarlanmış `Message` ve `clientCredentialType` ayarlanmış `Windows`. <xref:System.Security.Permissions.PrincipalPermissionAttribute> Her hizmet yönteme uygulanır ve her işlem için erişimi kısıtlamak için kullanılır. Çağıranın her işlem erişmek için bir Windows Yöneticisi olması gerekir.  
  
 Bu örnekte, istemci bir konsol uygulaması (.exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Hizmet yapılandırma dosyasını kullanan [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) ayarlanacak `principalPermissionMode` özniteliği:  
  
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
  
 Ayarı `principalPermissionMode` için `UseWindowsGroups` kullanımını etkinleştirir <xref:System.Security.Permissions.PrincipalPermissionAttribute> Windows grubu adlarına göre.  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> Her işlem aşağıdaki örnek kodda gösterildiği gibi çağıranın Windows administrators grubunun bir parçası olmasını gerektirecek şekilde uygulanır.  
  
```csharp
[PrincipalPermission(SecurityAction.Demand,   
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. Yöneticiler grubunun bir parçası olan bir hesabı altında çalışıyorsa, istemci her işlemi ile başarıyla iletişim kurar; Aksi takdirde, erişim reddedildi. Yetkilendirme hatası ile denemeler yapmak için istemci Yöneticiler grubunun bir parçası olmayan bir hesap altında çalıştırın. Konsol penceresinde istemci kapatmak için ENTER tuşuna basın.  
  
 Hizmet yetkilendirme hatalarının uygulayarak bildirilebilir bir <xref:System.ServiceModel.Dispatcher.IErrorHandler>. Bkz: [genişletme denetiminin üzerine hata işleme ve Raporlama](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) uygulama hakkında bilgi için `IErrorHandler`.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.
