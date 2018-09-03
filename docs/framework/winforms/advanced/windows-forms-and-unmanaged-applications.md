---
title: Windows Forms ve Yönetilmeyen Uygulamalar
ms.date: 03/30/2017
helpviewer_keywords:
- ActiveX controls [Windows Forms]
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- Windows Forms, interop
ms.assetid: 81bc100c-fa49-4614-85a6-0f7ab59eac8a
ms.openlocfilehash: bc0c848d1c92871dacab93497c674645f3ac83fe
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43463945"
---
# <a name="windows-forms-and-unmanaged-applications"></a><span data-ttu-id="88e2f-102">Windows Forms ve Yönetilmeyen Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="88e2f-102">Windows Forms and Unmanaged Applications</span></span>
<span data-ttu-id="88e2f-103">Windows Forms uygulamaları ve denetimleri bazı uyarılar ile yönetilmeyen uygulamalar ile çalışabilirler.</span><span class="sxs-lookup"><span data-stu-id="88e2f-103">Windows Forms applications and controls can interoperate with unmanaged applications, with some caveats.</span></span> <span data-ttu-id="88e2f-104">Aşağıdaki bölümlerde, Windows Forms uygulamalarının ve denetimlerinin destekleyen ve destekledikleri değil, senaryolar ve yapılandırmaları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="88e2f-104">The following sections describe the scenarios and configurations that Windows Forms applications and controls support and those that they do not support.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="88e2f-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="88e2f-105">In This Section</span></span>  
 [<span data-ttu-id="88e2f-106">Windows Forms ve Yönetilmeyen Uygulamalara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="88e2f-106">Windows Forms and Unmanaged Applications Overview</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)  
 <span data-ttu-id="88e2f-107">Yönetilmeyen uygulamalar ile çalışan Windows Forms denetimleri uygulayın ve nasıl kullanılacağı hakkında genel bilgiler sunar.</span><span class="sxs-lookup"><span data-stu-id="88e2f-107">Offers general information about how to use and implement Windows Forms controls that work with unmanaged applications.</span></span>  
  
 [<span data-ttu-id="88e2f-108">Nasıl yapılır: ShowDialog Yöntemi ile bir Windows Formunu Görüntüleyerek COM Birlikte Çalışmasını Destekleme</span><span class="sxs-lookup"><span data-stu-id="88e2f-108">How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method</span></span>](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 <span data-ttu-id="88e2f-109">Nasıl kullanılacağını gösteren bir kod örneği sunar <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> yönetilmeyen bir uygulamada bir Windows Form çalıştırmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="88e2f-109">Provides a code example that shows how to use the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to run a Windows Form in an unmanaged application.</span></span>  
  
 [<span data-ttu-id="88e2f-110">Nasıl yapılır: Her Windows Formunu Kendi İş Parçacığında Görüntüleyerek COM Birlikte Çalışmasını Destekleme</span><span class="sxs-lookup"><span data-stu-id="88e2f-110">How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread</span></span>](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 <span data-ttu-id="88e2f-111">Bir Windows formunu kendi iş parçacığında çalıştırmak üzere nasıl oluşturulduğunu gösteren bir kod örneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="88e2f-111">Provides a code example that shows how to run a Windows Form on its own thread.</span></span>  
  
 <span data-ttu-id="88e2f-112">Ayrıca bkz: [izlenecek yol: COM birlikte çalışabilirlik destekleyen görüntüleme her Windows formunu kendi kendi iş parçacığı üzerinde tarafından](https://msdn.microsoft.com/library/ms233639\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="88e2f-112">Also see [Walkthrough: Supporting COM Interop by Displaying Each Windows Form on Its Own Thread](https://msdn.microsoft.com/library/ms233639\(v=vs.110\)).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="88e2f-113">Başvuru</span><span class="sxs-lookup"><span data-stu-id="88e2f-113">Reference</span></span>  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType>  
 <span data-ttu-id="88e2f-114">Windows Form için ayrı bir iş parçacığı oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="88e2f-114">Used to create a separate thread for a Windows Form.</span></span>  
  
 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>  
 <span data-ttu-id="88e2f-115">Bir iş parçacığı için bir ileti döngüsü başlatır.</span><span class="sxs-lookup"><span data-stu-id="88e2f-115">Starts a message loop for a thread.</span></span>  
  
 <xref:System.Windows.Forms.Control.Invoke%2A>  
 <span data-ttu-id="88e2f-116">Bir form için yönetilmeyen bir uygulamadan çağrıları sürekliliğe devreder.</span><span class="sxs-lookup"><span data-stu-id="88e2f-116">Marshals calls from an unmanaged application to a form.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="88e2f-117">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="88e2f-117">Related Sections</span></span>  
 [<span data-ttu-id="88e2f-118">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="88e2f-118">Exposing .NET Framework Components to COM</span></span>](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 <span data-ttu-id="88e2f-119">Yönetilmeyen uygulamalarda .NET Framework türlerini kullanımı hakkında genel bilgi sunar.</span><span class="sxs-lookup"><span data-stu-id="88e2f-119">Offers general information about how to use .NET Framework types in unmanaged applications.</span></span>
