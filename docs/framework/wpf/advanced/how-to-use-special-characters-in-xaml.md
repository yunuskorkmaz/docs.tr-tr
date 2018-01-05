---
title: "Nasıl yapılır: XAML'de Özel Karakterler Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Unicode UTF-8 file format
- UTF-8 file format
- characters [WPF], special
- typography [WPF], special characters
- special characters [WPF]
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 79df87d716224cb8681c1688d94fe56077452c1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-special-characters-in-xaml"></a><span data-ttu-id="874c4-102">Nasıl yapılır: XAML'de Özel Karakterler Kullanma</span><span class="sxs-lookup"><span data-stu-id="874c4-102">How to: Use Special Characters in XAML</span></span>
<span data-ttu-id="874c4-103">Oluşturulan biçimlendirme dosyaları [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] otomatik olarak kaydedilir [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] vurgu işaretleri gibi en özel karakterleri düzgün şekilde kodlanmış anlamına gelen UTF-8 dosya biçimi.</span><span class="sxs-lookup"><span data-stu-id="874c4-103">Markup files that are created in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] are automatically saved in the [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF-8 file format, which means that most special characters, such as accent marks, are encoded correctly.</span></span> <span data-ttu-id="874c4-104">Ancak, farklı şekilde ele alınan yaygın olarak kullanılan özel karakter kümesi yok.</span><span class="sxs-lookup"><span data-stu-id="874c4-104">However, there is a set of commonly-used special characters that are handled differently.</span></span> <span data-ttu-id="874c4-105">Şu özel karakterleri izleyin [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] kodlama için standart.</span><span class="sxs-lookup"><span data-stu-id="874c4-105">These special characters follow the [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)][!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standard for encoding.</span></span>  
  
 <span data-ttu-id="874c4-106">Aşağıdaki tabloda, bu özel karakter kümesi kodlaması sözdizimi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="874c4-106">The following table shows the syntax for encoding this set of special characters:</span></span>  
  
|<span data-ttu-id="874c4-107">Karakter</span><span class="sxs-lookup"><span data-stu-id="874c4-107">Character</span></span>|<span data-ttu-id="874c4-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="874c4-108">Syntax</span></span>|<span data-ttu-id="874c4-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="874c4-109">Description</span></span>|  
|---------------|------------|-----------------|  
|<|`<`|<span data-ttu-id="874c4-110">Küçüktür simgesi</span><span class="sxs-lookup"><span data-stu-id="874c4-110">Less than symbol.</span></span>|  
|>|`>`|<span data-ttu-id="874c4-111">Büyüktür işareti.</span><span class="sxs-lookup"><span data-stu-id="874c4-111">Greater than sign.</span></span>|  
|&|`&`|<span data-ttu-id="874c4-112">Ampersan simgesi.</span><span class="sxs-lookup"><span data-stu-id="874c4-112">Ampersand symbol.</span></span>|  
|<span data-ttu-id="874c4-113">"</span><span class="sxs-lookup"><span data-stu-id="874c4-113">"</span></span>|`"`|<span data-ttu-id="874c4-114">Çift tırnak işareti simge.</span><span class="sxs-lookup"><span data-stu-id="874c4-114">Double quote symbol.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="874c4-115">Bir metin kullanarak biçimlendirme dosyası Düzenleyicisi gibi oluşturursanız, [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] not defteri dosyasında kaydetmelisiniz [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] herhangi korumak için UTF-8 dosya biçiminde kodlanmış özel karakter.</span><span class="sxs-lookup"><span data-stu-id="874c4-115">If you create a markup file using a text editor, such as [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Notepad, you must save the file in the [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF-8 file format in order to preserve any encoded special characters.</span></span>  
  
 <span data-ttu-id="874c4-116">Aşağıdaki örnek, nasıl özel karakterler metin biçimlendirme oluştururken kullanabileceğiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="874c4-116">The following example shows how you can use special characters in text when creating markup.</span></span>  
  
## <a name="example"></a><span data-ttu-id="874c4-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="874c4-117">Example</span></span>  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
