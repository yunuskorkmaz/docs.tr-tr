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
ms.openlocfilehash: 713428adc2e1576d1b95984b492fe84c042c0a09
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919636"
---
# <a name="how-to-use-special-characters-in-xaml"></a><span data-ttu-id="6f7ff-102">Nasıl yapılır: XAML'de Özel Karakterler Kullanma</span><span class="sxs-lookup"><span data-stu-id="6f7ff-102">How to: Use Special Characters in XAML</span></span>
<span data-ttu-id="6f7ff-103">Visual Studio 'da oluşturulan biçimlendirme dosyaları Unicode UTF-8 dosya biçiminde otomatik olarak kaydedilir, bu da vurgu işaretleri gibi çok sayıda özel karakterin doğru kodlandığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6f7ff-103">Markup files that are created in Visual Studio are automatically saved in the Unicode UTF-8 file format, which means that most special characters, such as accent marks, are encoded correctly.</span></span> <span data-ttu-id="6f7ff-104">Ancak, farklı şekilde işlenen yaygın olarak kullanılan özel karakterlerin bir kümesi vardır.</span><span class="sxs-lookup"><span data-stu-id="6f7ff-104">However, there is a set of commonly-used special characters that are handled differently.</span></span> <span data-ttu-id="6f7ff-105">Bu özel karakterler kodlama için World Wide Web Konsorsiyumu (W3C) [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standardını izler.</span><span class="sxs-lookup"><span data-stu-id="6f7ff-105">These special characters follow the World Wide Web Consortium (W3C) [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standard for encoding.</span></span>  
  
 <span data-ttu-id="6f7ff-106">Aşağıdaki tabloda, bu özel karakter kümesini kodlamaya yönelik sözdizimi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="6f7ff-106">The following table shows the syntax for encoding this set of special characters:</span></span>  
  
|<span data-ttu-id="6f7ff-107">Karakter</span><span class="sxs-lookup"><span data-stu-id="6f7ff-107">Character</span></span>|<span data-ttu-id="6f7ff-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f7ff-108">Syntax</span></span>|<span data-ttu-id="6f7ff-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f7ff-109">Description</span></span>|  
|---------------|------------|-----------------|  
|<|`&lt;`|<span data-ttu-id="6f7ff-110">Küçüktür simgesi.</span><span class="sxs-lookup"><span data-stu-id="6f7ff-110">Less than symbol.</span></span>|  
|>|`&gt;`|<span data-ttu-id="6f7ff-111">Büyüktür işareti.</span><span class="sxs-lookup"><span data-stu-id="6f7ff-111">Greater than sign.</span></span>|  
|&|`&amp;`|<span data-ttu-id="6f7ff-112">Ve simgesi.</span><span class="sxs-lookup"><span data-stu-id="6f7ff-112">Ampersand symbol.</span></span>|  
|<span data-ttu-id="6f7ff-113">"</span><span class="sxs-lookup"><span data-stu-id="6f7ff-113">"</span></span>|`&quot;`|<span data-ttu-id="6f7ff-114">Çift tırnak simgesi.</span><span class="sxs-lookup"><span data-stu-id="6f7ff-114">Double quote symbol.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="6f7ff-115">Windows Not Defteri gibi bir metin düzenleyicisi kullanarak bir biçimlendirme dosyası oluşturursanız, kodlanmış özel karakterleri korumak için dosyayı Unicode UTF-8 dosya biçiminde kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="6f7ff-115">If you create a markup file using a text editor, such as Windows Notepad, you must save the file in the Unicode UTF-8 file format in order to preserve any encoded special characters.</span></span>  
  
 <span data-ttu-id="6f7ff-116">Aşağıdaki örnek, biçimlendirme oluştururken metindeki özel karakterleri nasıl kullanabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f7ff-116">The following example shows how you can use special characters in text when creating markup.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f7ff-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="6f7ff-117">Example</span></span>  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
