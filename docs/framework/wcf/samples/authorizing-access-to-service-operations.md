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
# <a name="authorizing-access-to-service-operations"></a><span data-ttu-id="009e0-102">Hizmet İşlemlerine Erişimi Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="009e0-102">Authorizing Access to Service Operations</span></span>
<span data-ttu-id="009e0-103">Bu örnek, [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) <xref:System.Security.Permissions.PrincipalPermissionAttribute> hizmet işlemlerine erişim yetkisi vermek için özniteliğinin kullanımını etkinleştirmek üzere öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="009e0-103">This sample demonstrates how to use the [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) to enable use of the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to authorize access to service operations.</span></span> <span data-ttu-id="009e0-104">Bu örnek, [kullanmaya](getting-started-sample.md) başlama örneğine dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="009e0-104">This sample is based on the [Getting Started](getting-started-sample.md) sample.</span></span> <span data-ttu-id="009e0-105">Hizmeti ve istemcisi kullanılarak yapılandırılır [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="009e0-105">The service and client are configured using the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="009e0-106">`mode`Öğesinin özniteliği [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) olarak ayarlanmıştır `Message` ve `clientCredentialType` olarak ayarlanmıştır `Windows` .</span><span class="sxs-lookup"><span data-stu-id="009e0-106">The `mode` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) has been set to `Message` and `clientCredentialType` has been set to `Windows`.</span></span> <span data-ttu-id="009e0-107"><xref:System.Security.Permissions.PrincipalPermissionAttribute>Her bir hizmet yöntemine uygulanır ve her bir işleme erişimi kısıtlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="009e0-107">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each service method and used to restrict access to each operation.</span></span> <span data-ttu-id="009e0-108">Çağıranın her bir işleme erişmesi için bir Windows Yöneticisi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="009e0-108">The caller must be a Windows administrator to access each operation.</span></span>  
  
 <span data-ttu-id="009e0-109">Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="009e0-109">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="009e0-110">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="009e0-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="009e0-111">Hizmet yapılandırma dosyası [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) özniteliğini ayarlamak için öğesini kullanır `principalPermissionMode` :</span><span class="sxs-lookup"><span data-stu-id="009e0-111">The service configuration file uses the [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) to set the `principalPermissionMode` attribute:</span></span>  
  
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
  
 <span data-ttu-id="009e0-112">İçin ayarı `principalPermissionMode` , `UseWindowsGroups` <xref:System.Security.Permissions.PrincipalPermissionAttribute> Windows Grup adlarına göre kullanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="009e0-112">Setting the `principalPermissionMode` to `UseWindowsGroups` enables the use of <xref:System.Security.Permissions.PrincipalPermissionAttribute> based on Windows group names.</span></span>  
  
 <span data-ttu-id="009e0-113">, <xref:System.Security.Permissions.PrincipalPermissionAttribute> Aşağıdaki örnek kodda gösterildiği gibi çağıranın Windows yöneticileri grubunun bir parçası olmasını gerektirmek için her bir işleme uygulanır.</span><span class="sxs-lookup"><span data-stu-id="009e0-113">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each operation to require the caller to be part of the Windows administrators group, as shown in the following sample code.</span></span>  
  
```csharp
[PrincipalPermission(SecurityAction.Demand,
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 <span data-ttu-id="009e0-114">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="009e0-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="009e0-115">İstemci, Yöneticiler grubunun parçası olan bir hesabın altında çalışıyorsa, her işlemle birlikte başarıyla iletişim kurar; Aksi takdirde, erişim reddedilir.</span><span class="sxs-lookup"><span data-stu-id="009e0-115">The client successfully communicates with each operation if it is running under an account that is part of the Administrators group; otherwise, access is denied.</span></span> <span data-ttu-id="009e0-116">Yetkilendirme hatasıyla denemeler yapmak için istemciyi Yöneticiler grubunun parçası olmayan bir hesap altında çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="009e0-116">To experiment with authorization failure, run the client under an account that is not part of the Administrators group.</span></span> <span data-ttu-id="009e0-117">İstemcisini kapatmak için konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="009e0-117">Press ENTER in the console window to shut down the client.</span></span>  
  
 <span data-ttu-id="009e0-118">Bir hizmet, bir hizmeti uygulayarak yetkilendirme hatalarından haberdar olabilir <xref:System.ServiceModel.Dispatcher.IErrorHandler> .</span><span class="sxs-lookup"><span data-stu-id="009e0-118">A service can be notified of authorization failures by implementing an <xref:System.ServiceModel.Dispatcher.IErrorHandler>.</span></span> <span data-ttu-id="009e0-119">Uygulama hakkında bilgi için bkz. [hata işleme ve raporlama üzerinde denetimi genişletme](extending-control-over-error-handling-and-reporting.md) `IErrorHandler` .</span><span class="sxs-lookup"><span data-stu-id="009e0-119">See [Extending Control Over Error Handling and Reporting](extending-control-over-error-handling-and-reporting.md) for information about implementing `IErrorHandler`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="009e0-120">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="009e0-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="009e0-121">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="009e0-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="009e0-122">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="009e0-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="009e0-123">Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="009e0-123">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
