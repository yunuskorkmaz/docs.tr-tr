---
title: Yönetilmeyen uygulamalar
ms.date: 03/30/2017
helpviewer_keywords:
- ActiveX controls [Windows Forms]
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- Windows Forms, interop
ms.assetid: 81bc100c-fa49-4614-85a6-0f7ab59eac8a
ms.openlocfilehash: 17dc20653d1628dfd460a9891e1b0a21c0ebecbd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746359"
---
# <a name="windows-forms-and-unmanaged-applications"></a><span data-ttu-id="933ce-102">Windows Forms ve Yönetilmeyen Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="933ce-102">Windows Forms and Unmanaged Applications</span></span>
<span data-ttu-id="933ce-103">Windows Forms uygulamalar ve denetimler, bazı uyarılarla yönetilmeyen uygulamalarla birlikte çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="933ce-103">Windows Forms applications and controls can interoperate with unmanaged applications, with some caveats.</span></span> <span data-ttu-id="933ce-104">Aşağıdaki bölümlerde, uygulamaları ve denetimleri Windows Forms uygulamalar ve denetimlerin desteklediği senaryolar ve Konfigürasyonlar açıklanır.</span><span class="sxs-lookup"><span data-stu-id="933ce-104">The following sections describe the scenarios and configurations that Windows Forms applications and controls support and those that they do not support.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="933ce-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="933ce-105">In This Section</span></span>  
 [<span data-ttu-id="933ce-106">Windows Forms ve Yönetilmeyen Uygulamalara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="933ce-106">Windows Forms and Unmanaged Applications Overview</span></span>](windows-forms-and-unmanaged-applications-overview.md)  
 <span data-ttu-id="933ce-107">, Yönetilmeyen uygulamalarla çalışan Windows Forms denetimlerinin kullanımı ve uygulanması hakkında genel bilgiler sunar.</span><span class="sxs-lookup"><span data-stu-id="933ce-107">Offers general information about how to use and implement Windows Forms controls that work with unmanaged applications.</span></span>  
  
 [<span data-ttu-id="933ce-108">Nasıl yapılır: ShowDialog Yöntemi ile bir Windows Formunu Görüntüleyerek COM Birlikte Çalışmasını Destekleme</span><span class="sxs-lookup"><span data-stu-id="933ce-108">How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method</span></span>](com-interop-by-displaying-a-windows-form-shadow.md)  
 <span data-ttu-id="933ce-109">Yönetilmeyen bir uygulamada Windows formunu çalıştırmak için <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> yönteminin nasıl kullanılacağını gösteren bir kod örneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="933ce-109">Provides a code example that shows how to use the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to run a Windows Form in an unmanaged application.</span></span>  
  
 [<span data-ttu-id="933ce-110">Nasıl yapılır: Her Windows Formunu Kendi İş Parçacığında Görüntüleyerek COM Birlikte Çalışmasını Destekleme</span><span class="sxs-lookup"><span data-stu-id="933ce-110">How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread</span></span>](how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 <span data-ttu-id="933ce-111">Kendi iş parçacığında bir Windows formunun nasıl çalıştırılacağını gösteren bir kod örneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="933ce-111">Provides a code example that shows how to run a Windows Form on its own thread.</span></span>  
  
 <span data-ttu-id="933ce-112">Ayrıca bkz. [Izlenecek yol: her Windows formunu kendi Iş parçacığında görüntüleyerek com birlikte çalışmasını destekleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="933ce-112">Also see [Walkthrough: Supporting COM Interop by Displaying Each Windows Form on Its Own Thread](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100)).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="933ce-113">Başvuru</span><span class="sxs-lookup"><span data-stu-id="933ce-113">Reference</span></span>  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType>  
 <span data-ttu-id="933ce-114">Bir Windows formu için ayrı bir iş parçacığı oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="933ce-114">Used to create a separate thread for a Windows Form.</span></span>  
  
 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>  
 <span data-ttu-id="933ce-115">İş parçacığı için bir ileti döngüsü başlatır.</span><span class="sxs-lookup"><span data-stu-id="933ce-115">Starts a message loop for a thread.</span></span>  
  
 <xref:System.Windows.Forms.Control.Invoke%2A>  
 <span data-ttu-id="933ce-116">Yönetilmeyen bir uygulamadan bir forma yapılan çağrı öğeleri.</span><span class="sxs-lookup"><span data-stu-id="933ce-116">Marshals calls from an unmanaged application to a form.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="933ce-117">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="933ce-117">Related Sections</span></span>  
 [<span data-ttu-id="933ce-118">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="933ce-118">Exposing .NET Framework Components to COM</span></span>](../../interop/exposing-dotnet-components-to-com.md)  
 <span data-ttu-id="933ce-119">Yönetilmeyen uygulamalarda .NET Framework türlerini kullanma hakkında genel bilgiler sunar.</span><span class="sxs-lookup"><span data-stu-id="933ce-119">Offers general information about how to use .NET Framework types in unmanaged applications.</span></span>
