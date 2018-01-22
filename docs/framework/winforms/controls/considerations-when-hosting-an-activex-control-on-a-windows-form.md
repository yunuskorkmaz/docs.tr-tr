---
title: "Bir Windows Formunda bir ActiveX Denetimi Barındırmayla İlgili Konular"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- ActiveX controls [Windows Forms], hosting
- Windows Forms, ActiveX controls
- Windows Forms, hosting ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 2509302d-a74e-484f-9890-2acdbfa67a68
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 23c8476e4013cca6d906d85f11658deddc585869
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="considerations-when-hosting-an-activex-control-on-a-windows-form"></a><span data-ttu-id="4fa07-102">Bir Windows Formunda bir ActiveX Denetimi Barındırmayla İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="4fa07-102">Considerations When Hosting an ActiveX Control on a Windows Form</span></span>
<span data-ttu-id="4fa07-103">Windows Forms ana bilgisayar Windows Forms denetimleri için optimize edilmiştir rağmen ActiveX denetimlerini kullanmaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4fa07-103">Although Windows Forms have been optimized to host Windows Forms controls, you can still use ActiveX controls.</span></span> <span data-ttu-id="4fa07-104">ActiveX denetimleri kullanan bir uygulamayı planlarken aşağıdaki noktaları göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="4fa07-104">Keep the following considerations in mind when planning an application that uses ActiveX controls:</span></span>  
  
-   <span data-ttu-id="4fa07-105">**Güvenlik** ortak dil çalışma zamanı kod erişim güvenliği açısından geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4fa07-105">**Security** The common language runtime has been enhanced with regard to code access security.</span></span> <span data-ttu-id="4fa07-106">Windows Forms özelliklerine sahip uygulamaları işlevselliğinin büyük kısmını erişilebilir ile sorun olmadan tam güvenilen bir ortamda ve yarı güvenilir bir ortamda çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="4fa07-106">Applications featuring Windows Forms can run in a fully trusted environment without issue and in a semi-trusted environment with most of the functionality accessible.</span></span> <span data-ttu-id="4fa07-107">Windows Forms denetimleri hiçbir zorluklar sahip tarayıcıda barındırılabilir.</span><span class="sxs-lookup"><span data-stu-id="4fa07-107">Windows Forms controls can be hosted in a browser with no complications.</span></span> <span data-ttu-id="4fa07-108">Ancak, Windows Forms ActiveX denetimlerinde bu güvenlik geliştirmeleri yararlanamaz.</span><span class="sxs-lookup"><span data-stu-id="4fa07-108">However, ActiveX controls on Windows Forms cannot take advantage of these security enhancements.</span></span> <span data-ttu-id="4fa07-109">Bir ActiveX denetimini çalıştırmak ile ayarlamak yönetilmeyen kod izni gerektirir <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="4fa07-109">Running an ActiveX control requires unmanaged code permission, which is set with the <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="4fa07-110">Güvenlik ve yönetilmeyen kod izin hakkında daha fazla bilgi için bkz: <xref:System.Security.Permissions.SecurityPermissionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4fa07-110">For more information about security and unmanaged code permission, see <xref:System.Security.Permissions.SecurityPermissionAttribute>.</span></span>  
  
-   <span data-ttu-id="4fa07-111">**Toplam sahip olma maliyetini** ActiveX denetimleri için Windows formu eklenen oluşturulan dosya boyutunu önemli ölçüde ekleyebilirsiniz bağlandığında bu Windows Form ile dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="4fa07-111">**Total Cost of Ownership** ActiveX controls added to a Windows Form are deployed with that Windows Form in their entirety, which can add significantly to the size of the file(s) created.</span></span> <span data-ttu-id="4fa07-112">Ayrıca, Windows formlarına ActiveX denetimlerini kullanarak kayıt defterine yazılıyor gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4fa07-112">Additionally, using ActiveX controls on Windows Forms requires writing to the registry.</span></span> <span data-ttu-id="4fa07-113">Bu gerektirmeyen Windows Forms denetimleri, bir kullanıcının bilgisayarına daha bozucu budur.</span><span class="sxs-lookup"><span data-stu-id="4fa07-113">This is more invasive to a user's computer than Windows Forms controls, which do not require this.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4fa07-114">ActiveX ile çalışma denetimi COM birlikte çalışma sarmalayıcısı kullanılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4fa07-114">Working with an ActiveX control requires the use of a COM interop wrapper.</span></span> <span data-ttu-id="4fa07-115">Daha fazla bilgi için bkz: [COM birlikte çalışabilirliği Visual Basic ve Visual C#](~/docs/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="4fa07-115">For more information, see [COM Interoperability in Visual Basic and Visual C#](~/docs/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4fa07-116">ActiveX denetiminin üyenin adını tanımlanan bir ad eşleşirse [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], ActiveX denetim içeri Aktarıcı ile üye adı ön eki sonra **Ctl** oluşturduğunda, <xref:System.Windows.Forms.AxHost> türetilmiş sınıf.</span><span class="sxs-lookup"><span data-stu-id="4fa07-116">If the name of a member of the ActiveX control matches a name defined in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], then the ActiveX Control Importer will prefix the member name with **Ctl** when it creates the <xref:System.Windows.Forms.AxHost> derived class.</span></span> <span data-ttu-id="4fa07-117">ActiveX denetimi adlı bir üye varsa, örneğin, **düzeni**, yeniden adlandırılır **CtlLayout** AxHost türetilmiş sınıfında çünkü **düzeni** olay içinde tanımlanmıştır [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4fa07-117">For example, if your ActiveX control has a member named **Layout**, it is renamed **CtlLayout** in the AxHost-derived class because the **Layout** event is defined within the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fa07-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4fa07-118">See Also</span></span>  
 [<span data-ttu-id="4fa07-119">Nasıl yapılır: Windows Forms’a ActiveX Denetimleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="4fa07-119">How to: Add ActiveX Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md)  
 [<span data-ttu-id="4fa07-120">Kod erişimi güvenliği</span><span class="sxs-lookup"><span data-stu-id="4fa07-120">Code Access Security</span></span>](../../../../docs/framework/misc/code-access-security.md)  
 [<span data-ttu-id="4fa07-121">Denetimleri ve çeşitli diller ve kitaplıkları karşılaştırıldığında programlanabilir nesneleri</span><span class="sxs-lookup"><span data-stu-id="4fa07-121">Controls and Programmable Objects Compared in Various Languages and Libraries</span></span>](http://msdn.microsoft.com/library/021f2a1b-8247-4348-a5ad-e1d9ab23004b)  
 [<span data-ttu-id="4fa07-122">Windows Forms’a Denetimler Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="4fa07-122">Putting Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)  
 [<span data-ttu-id="4fa07-123">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="4fa07-123">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)
