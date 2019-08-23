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
ms.openlocfilehash: 61ee38319b2f0aa46690fb063f6ffe6612f993ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918445"
---
# <a name="how-to-use-special-characters-in-xaml"></a><span data-ttu-id="bf0d1-102">Nasıl yapılır: XAML'de Özel Karakterler Kullanma</span><span class="sxs-lookup"><span data-stu-id="bf0d1-102">How to: Use Special Characters in XAML</span></span>
<span data-ttu-id="bf0d1-103">İçinde [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] oluşturulan biçimlendirme dosyaları [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF-8 dosya biçiminde otomatik olarak kaydedilir, bu da vurgu işaretleri gibi en özel karakterlerin doğru şekilde kodlanmasıdır.</span><span class="sxs-lookup"><span data-stu-id="bf0d1-103">Markup files that are created in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] are automatically saved in the [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF-8 file format, which means that most special characters, such as accent marks, are encoded correctly.</span></span> <span data-ttu-id="bf0d1-104">Ancak, farklı şekilde işlenen yaygın olarak kullanılan özel karakterlerin bir kümesi vardır.</span><span class="sxs-lookup"><span data-stu-id="bf0d1-104">However, there is a set of commonly-used special characters that are handled differently.</span></span> <span data-ttu-id="bf0d1-105">Bu özel karakterler, [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] kodlama için standardı izler.</span><span class="sxs-lookup"><span data-stu-id="bf0d1-105">These special characters follow the [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standard for encoding.</span></span>  
  
 <span data-ttu-id="bf0d1-106">Aşağıdaki tabloda, bu özel karakter kümesini kodlamaya yönelik sözdizimi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="bf0d1-106">The following table shows the syntax for encoding this set of special characters:</span></span>  
  
|<span data-ttu-id="bf0d1-107">Karakter</span><span class="sxs-lookup"><span data-stu-id="bf0d1-107">Character</span></span>|<span data-ttu-id="bf0d1-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bf0d1-108">Syntax</span></span>|<span data-ttu-id="bf0d1-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf0d1-109">Description</span></span>|  
|---------------|------------|-----------------|  
|<|`&lt;`|<span data-ttu-id="bf0d1-110">Küçüktür simgesi.</span><span class="sxs-lookup"><span data-stu-id="bf0d1-110">Less than symbol.</span></span>|  
|>|`&gt;`|<span data-ttu-id="bf0d1-111">Büyüktür işareti.</span><span class="sxs-lookup"><span data-stu-id="bf0d1-111">Greater than sign.</span></span>|  
|&|`&amp;`|<span data-ttu-id="bf0d1-112">Ve simgesi.</span><span class="sxs-lookup"><span data-stu-id="bf0d1-112">Ampersand symbol.</span></span>|  
|<span data-ttu-id="bf0d1-113">"</span><span class="sxs-lookup"><span data-stu-id="bf0d1-113">"</span></span>|`&quot;`|<span data-ttu-id="bf0d1-114">Çift tırnak simgesi.</span><span class="sxs-lookup"><span data-stu-id="bf0d1-114">Double quote symbol.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="bf0d1-115">Windows Not Defteri gibi bir metin düzenleyicisi kullanarak bir biçimlendirme dosyası oluşturursanız, kodlanmış özel karakterleri korumak için dosyayı [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF-8 dosya biçiminde kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="bf0d1-115">If you create a markup file using a text editor, such as Windows Notepad, you must save the file in the [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF-8 file format in order to preserve any encoded special characters.</span></span>  
  
 <span data-ttu-id="bf0d1-116">Aşağıdaki örnek, biçimlendirme oluştururken metindeki özel karakterleri nasıl kullanabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf0d1-116">The following example shows how you can use special characters in text when creating markup.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf0d1-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="bf0d1-117">Example</span></span>  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
