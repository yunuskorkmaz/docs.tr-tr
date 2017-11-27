---
title: "Hizmet İşlemlerine Erişimi Yetkilendirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
caps.latest.revision: "23"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cfa1eefa9f7bd940baf3796d92ac7b49e0f9843e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="authorizing-access-to-service-operations"></a><span data-ttu-id="119ac-102">Hizmet İşlemlerine Erişimi Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="119ac-102">Authorizing Access to Service Operations</span></span>
<span data-ttu-id="119ac-103">Bu örnek nasıl kullanılacağı ortaya [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) kullanımını etkinleştirmek için <xref:System.Security.Permissions.PrincipalPermissionAttribute> hizmet işlemlerine erişimi yetkilendirmek için öznitelik.</span><span class="sxs-lookup"><span data-stu-id="119ac-103">This sample demonstrates how to use the [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to enable use of the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to authorize access to service operations.</span></span> <span data-ttu-id="119ac-104">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="119ac-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) sample.</span></span> <span data-ttu-id="119ac-105">İstemci ve hizmet kullanılarak yapılandırılmış olan [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="119ac-105">The service and client are configured using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="119ac-106">`mode` Özniteliği [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) ayarlandığından `Message` ve `clientCredentialType` ayarlandığından `Windows`.</span><span class="sxs-lookup"><span data-stu-id="119ac-106">The `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) has been set to `Message` and `clientCredentialType` has been set to `Windows`.</span></span> <span data-ttu-id="119ac-107"><xref:System.Security.Permissions.PrincipalPermissionAttribute> Her hizmet yöntemi uygulanır ve her işlem için erişimi kısıtlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="119ac-107">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each service method and used to restrict access to each operation.</span></span> <span data-ttu-id="119ac-108">Çağıran, her işlem erişmek için bir Windows yöneticisi olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="119ac-108">The caller must be a Windows administrator to access each operation.</span></span>  
  
 <span data-ttu-id="119ac-109">Bu örnekte, istemci bir konsol uygulaması (.exe) ve Internet Information Services (IIS) tarafından barındırılan hizmetindeki.</span><span class="sxs-lookup"><span data-stu-id="119ac-109">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="119ac-110">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="119ac-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="119ac-111">Hizmet yapılandırma dosyası kullanan [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) ayarlamak için `principalPermissionMode` özniteliği:</span><span class="sxs-lookup"><span data-stu-id="119ac-111">The service configuration file uses the [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to set the `principalPermissionMode` attribute:</span></span>  
  
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
  
 <span data-ttu-id="119ac-112">Ayarı `principalPermissionMode` için `UseWindowsGroups` kullanmayı sağlayan <xref:System.Security.Permissions.PrincipalPermissionAttribute> Windows grup adlarını temel alarak.</span><span class="sxs-lookup"><span data-stu-id="119ac-112">Setting the `principalPermissionMode` to `UseWindowsGroups` enables the use of <xref:System.Security.Permissions.PrincipalPermissionAttribute> based on Windows group names.</span></span>  
  
 <span data-ttu-id="119ac-113"><xref:System.Security.Permissions.PrincipalPermissionAttribute> Aşağıdaki örnek kodda gösterildiği gibi Windows administrators grubunun bir parçası olarak çağıran gerektirecek şekilde her bir işlemin uygulanır.</span><span class="sxs-lookup"><span data-stu-id="119ac-113">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each operation to require the caller to be part of the Windows administrators group, as shown in the following sample code.</span></span>  
  
```  
[PrincipalPermission(SecurityAction.Demand,   
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 <span data-ttu-id="119ac-114">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="119ac-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="119ac-115">Yöneticiler grubunun bir parçası olan bir hesabı altında çalışıyorsa, istemci başarıyla her işlemi ile iletişim kurar; Aksi takdirde, erişim reddedildi.</span><span class="sxs-lookup"><span data-stu-id="119ac-115">The client successfully communicates with each operation if it is running under an account that is part of the Administrators group; otherwise, access is denied.</span></span> <span data-ttu-id="119ac-116">Yetkilendirme hatası ile denemek için Administrators grubunun parçası olmayan bir hesap altında istemci çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="119ac-116">To experiment with authorization failure, run the client under an account that is not part of the Administrators group.</span></span> <span data-ttu-id="119ac-117">Konsol penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="119ac-117">Press ENTER in the console window to shut down the client.</span></span>  
  
 <span data-ttu-id="119ac-118">Bir hizmet uygulayarak yetkilendirme hatalarının bildirilebilir bir <xref:System.ServiceModel.Dispatcher.IErrorHandler>.</span><span class="sxs-lookup"><span data-stu-id="119ac-118">A service can be notified of authorization failures by implementing an <xref:System.ServiceModel.Dispatcher.IErrorHandler>.</span></span> <span data-ttu-id="119ac-119">Bkz: [genişletme denetim üzerinden hata işleme ve Raporlama](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) uygulama hakkında bilgi için `IErrorHandler`.</span><span class="sxs-lookup"><span data-stu-id="119ac-119">See [Extending Control Over Error Handling and Reporting](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) for information about implementing `IErrorHandler`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="119ac-120">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="119ac-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="119ac-121">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="119ac-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="119ac-122">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="119ac-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="119ac-123">Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="119ac-123">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="119ac-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="119ac-124">See Also</span></span>
