---
title: "Nasıl yapılır: XAML'de Özel Karakterler Kullanma"
ms.date: 03/30/2017
helpviewer_keywords:
- Unicode UTF-8 file format
- UTF-8 file format
- characters [WPF], special
- typography [WPF], special characters
- special characters [WPF]
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
ms.openlocfilehash: 18934e06f45ca4b88f48bce8a310a07b460a5f53
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051101"
---
# <a name="how-to-use-special-characters-in-xaml"></a><span data-ttu-id="92581-102">Nasıl yapılır: XAML'de Özel Karakterler Kullanma</span><span class="sxs-lookup"><span data-stu-id="92581-102">How to: Use Special Characters in XAML</span></span>
<span data-ttu-id="92581-103">Oluşturulan biçimlendirme dosyalarında biçimlendirmeyi [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] otomatik olarak kaydedilir [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] vurgu işaretleri gibi çoğu özel karakteri doğru kodlanmış anlamına gelen UTF-8 dosya biçimi.</span><span class="sxs-lookup"><span data-stu-id="92581-103">Markup files that are created in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] are automatically saved in the [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF-8 file format, which means that most special characters, such as accent marks, are encoded correctly.</span></span> <span data-ttu-id="92581-104">Ancak, bir dizi farklı şekilde ele alınan sık kullanılan özel karakterler var.</span><span class="sxs-lookup"><span data-stu-id="92581-104">However, there is a set of commonly-used special characters that are handled differently.</span></span> <span data-ttu-id="92581-105">Bu özel karakterlerin izleyin [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] kodlama standardı.</span><span class="sxs-lookup"><span data-stu-id="92581-105">These special characters follow the [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standard for encoding.</span></span>  
  
 <span data-ttu-id="92581-106">Aşağıdaki tabloda, bu özel karakter kümesi kodlaması için sözdizimi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92581-106">The following table shows the syntax for encoding this set of special characters:</span></span>  
  
|<span data-ttu-id="92581-107">Karakter</span><span class="sxs-lookup"><span data-stu-id="92581-107">Character</span></span>|<span data-ttu-id="92581-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="92581-108">Syntax</span></span>|<span data-ttu-id="92581-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92581-109">Description</span></span>|  
|---------------|------------|-----------------|  
|<|`&lt;`|<span data-ttu-id="92581-110">Küçük simge.</span><span class="sxs-lookup"><span data-stu-id="92581-110">Less than symbol.</span></span>|  
|>|`&gt;`|<span data-ttu-id="92581-111">Büyüktür işareti.</span><span class="sxs-lookup"><span data-stu-id="92581-111">Greater than sign.</span></span>|  
|&|`&amp;`|<span data-ttu-id="92581-112">Ampersan simgesi.</span><span class="sxs-lookup"><span data-stu-id="92581-112">Ampersand symbol.</span></span>|  
|<span data-ttu-id="92581-113">"</span><span class="sxs-lookup"><span data-stu-id="92581-113">"</span></span>|`&quot;`|<span data-ttu-id="92581-114">Çift tırnak işareti sembolü.</span><span class="sxs-lookup"><span data-stu-id="92581-114">Double quote symbol.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="92581-115">Biçimlendirme dosyası kullanarak bir metin düzenleyicisi gibi oluşturursanız [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] not defteri dosyasında kaydetmelisiniz [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] herhangi korumak için dosya biçimi UTF-8 kodlamalı özel karakterler.</span><span class="sxs-lookup"><span data-stu-id="92581-115">If you create a markup file using a text editor, such as [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Notepad, you must save the file in the [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF-8 file format in order to preserve any encoded special characters.</span></span>  
  
 <span data-ttu-id="92581-116">Aşağıdaki örnekte, nasıl özel karakterler metin biçimlendirme oluştururken kullanabileceğiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="92581-116">The following example shows how you can use special characters in text when creating markup.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92581-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="92581-117">Example</span></span>  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
