---
title: 'Azaltma: Yol iki nokta üst üste denetimleri'
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e41a51dcdf243091d3962278f1a59a85a2722894
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66251126"
---
# <a name="mitigation-path-colon-checks"></a><span data-ttu-id="643db-102">Azaltma: Yol iki nokta üst üste denetimleri</span><span class="sxs-lookup"><span data-stu-id="643db-102">Mitigation: Path Colon Checks</span></span>
<span data-ttu-id="643db-103">.NET Framework 4.6.2'yi hedefleyen uygulamalar ile başlayarak, önceden desteklenmeyen yolları (hem uzunluğu ve biçim açısından) desteklemek için bir dizi değişiklik yapıldı.</span><span class="sxs-lookup"><span data-stu-id="643db-103">Starting with apps that target the .NET Framework 4.6.2, a number of changes were made to support previously unsupported paths (both in terms of length and format).</span></span> <span data-ttu-id="643db-104">Özellikle, denetimleri uygun sürücü ayırıcı sözdizimi (iki nokta üst üste) için daha doğru yapıldı.</span><span class="sxs-lookup"><span data-stu-id="643db-104">In particular, checks for the proper drive separator syntax (the colon) were made more correct.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="643db-105">Etki</span><span class="sxs-lookup"><span data-stu-id="643db-105">Impact</span></span>  
 <span data-ttu-id="643db-106">Bazı URI yollarını bu değişiklikleri engellemeye <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> ve <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> daha önce desteklenen yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="643db-106">These changes block some URI paths the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods previously supported.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="643db-107">Azaltma</span><span class="sxs-lookup"><span data-stu-id="643db-107">Mitigation</span></span>  
 <span data-ttu-id="643db-108">Tarafından artık desteklenmeyen daha önce kabul edilebilir bir yolu, sorunu gidermek için <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> ve <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> yöntemleri, aşağıdakileri yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="643db-108">To work around the problem of a previously acceptable path that is no longer supported by the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods, you can do the following:</span></span>  
  
- <span data-ttu-id="643db-109">El ile bir URL'den düzeni kaldırın.</span><span class="sxs-lookup"><span data-stu-id="643db-109">Manually remove the scheme from a URL.</span></span> <span data-ttu-id="643db-110">Örneğin, kaldırma `file://` bir URL'den.</span><span class="sxs-lookup"><span data-stu-id="643db-110">For example, remove `file://` from a URL.</span></span>  
  
- <span data-ttu-id="643db-111">URI başarılı bir <xref:System.Uri> oluşturucusu ve değerini alma <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="643db-111">Pass the URI to a <xref:System.Uri> constructor,  and retrieve the value of the <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> property.</span></span>  
  
- <span data-ttu-id="643db-112">Yeni yol normalleştirme dışında ayarlayarak iyileştirilmiş `Switch.System.IO.UseLegacyPathHandling` <xref:System.AppContext> geçin `true`.</span><span class="sxs-lookup"><span data-stu-id="643db-112">Opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> switch to `true`.</span></span>  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
    </runtime>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="643db-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="643db-113">See also</span></span>

- [<span data-ttu-id="643db-114">Yeniden Hedefleme Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="643db-114">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
