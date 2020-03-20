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
# <a name="authorizing-access-to-service-operations"></a><span data-ttu-id="0511f-102">Hizmet İşlemlerine Erişimi Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="0511f-102">Authorizing Access to Service Operations</span></span>
<span data-ttu-id="0511f-103">Bu örnek, hizmet işlemlerine <xref:System.Security.Permissions.PrincipalPermissionAttribute> [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) erişimi yetkilendirmek için özniteliğin kullanımını etkinleştirmek için serviceAuthorization>'nin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0511f-103">This sample demonstrates how to use the [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to enable use of the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to authorize access to service operations.</span></span> <span data-ttu-id="0511f-104">Bu örnek [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) örneği dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0511f-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) sample.</span></span> <span data-ttu-id="0511f-105">Hizmet ve istemci [ \<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)kullanılarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="0511f-105">The service and client are configured using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="0511f-106">`mode` `Message` `clientCredentialType` `Windows` [Güvenlik>özniteliği ayarlandı ve '' \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) olarak ayarlandı.</span><span class="sxs-lookup"><span data-stu-id="0511f-106">The `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) has been set to `Message` and `clientCredentialType` has been set to `Windows`.</span></span> <span data-ttu-id="0511f-107">Her <xref:System.Security.Permissions.PrincipalPermissionAttribute> hizmet yöntemine uygulanır ve her işlemiçin erişimi kısıtlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0511f-107">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each service method and used to restrict access to each operation.</span></span> <span data-ttu-id="0511f-108">Arayan her işlem erişmek için bir Windows yöneticisi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0511f-108">The caller must be a Windows administrator to access each operation.</span></span>  
  
 <span data-ttu-id="0511f-109">Bu örnekte, istemci bir konsol uygulamasıdır (.exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="0511f-109">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0511f-110">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="0511f-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="0511f-111">Hizmet yapılandırma dosyası, özniteliği ayarlamak `principalPermissionMode` için [ \<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) kullanır:</span><span class="sxs-lookup"><span data-stu-id="0511f-111">The service configuration file uses the [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to set the `principalPermissionMode` attribute:</span></span>  
  
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
  
 <span data-ttu-id="0511f-112">Windows `principalPermissionMode` grup `UseWindowsGroups` adlarını <xref:System.Security.Permissions.PrincipalPermissionAttribute> temel alan kullanımını etkinleştirmek için ayarlama.</span><span class="sxs-lookup"><span data-stu-id="0511f-112">Setting the `principalPermissionMode` to `UseWindowsGroups` enables the use of <xref:System.Security.Permissions.PrincipalPermissionAttribute> based on Windows group names.</span></span>  
  
 <span data-ttu-id="0511f-113">Aşağıdaki <xref:System.Security.Permissions.PrincipalPermissionAttribute> örnek kodda gösterildiği gibi, arayanın Windows yöneticileri grubunun bir parçası olmasını gerektiren her işlem uygulanır.</span><span class="sxs-lookup"><span data-stu-id="0511f-113">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each operation to require the caller to be part of the Windows administrators group, as shown in the following sample code.</span></span>  
  
```csharp
[PrincipalPermission(SecurityAction.Demand,
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 <span data-ttu-id="0511f-114">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0511f-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="0511f-115">İstemci, Yöneticiler grubunun bir parçası olan bir hesap altında çalışıyorsa, her işlemle başarılı bir şekilde iletişim kurar; aksi takdirde, erişim reddedilir.</span><span class="sxs-lookup"><span data-stu-id="0511f-115">The client successfully communicates with each operation if it is running under an account that is part of the Administrators group; otherwise, access is denied.</span></span> <span data-ttu-id="0511f-116">Yetkilendirme hatasıyla denemeler yapmak için istemciyi Yöneticiler grubunun parçası olmayan bir hesap altında çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0511f-116">To experiment with authorization failure, run the client under an account that is not part of the Administrators group.</span></span> <span data-ttu-id="0511f-117">İstemciyi kapatmak için konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="0511f-117">Press ENTER in the console window to shut down the client.</span></span>  
  
 <span data-ttu-id="0511f-118">Bir hizmet, bir <xref:System.ServiceModel.Dispatcher.IErrorHandler>.</span><span class="sxs-lookup"><span data-stu-id="0511f-118">A service can be notified of authorization failures by implementing an <xref:System.ServiceModel.Dispatcher.IErrorHandler>.</span></span> <span data-ttu-id="0511f-119">Uygulama hakkında bilgi için [Hata İşleme ve Raporlama Üzerinde Denetimi Genişletme'ye](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) `IErrorHandler`bakın.</span><span class="sxs-lookup"><span data-stu-id="0511f-119">See [Extending Control Over Error Handling and Reporting](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) for information about implementing `IErrorHandler`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0511f-120">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="0511f-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="0511f-121">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="0511f-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="0511f-122">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="0511f-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="0511f-123">Örneği tek veya bilgisayar lar arası yapılandırmada çalıştırmak [için, Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="0511f-123">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
