---
title: "Nasıl yapılır: XAML'de Özel Karakterler Kullanma"
description: Windows Presentation Foundation XAML dosyalarında kullanılmak üzere Visual Studio 'da Unicode UTF-8 dosya biçimindeki özel karakterleri kodlamaya yönelik sözdizimi hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- Unicode UTF-8 file format
- UTF-8 file format
- characters [WPF], special
- typography [WPF], special characters
- special characters [WPF]
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
ms.openlocfilehash: ac2388fd96aa26ddd99408ac9f847ce517958568
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168360"
---
# <a name="how-to-use-special-characters-in-xaml"></a><span data-ttu-id="89023-103">Nasıl yapılır: XAML'de Özel Karakterler Kullanma</span><span class="sxs-lookup"><span data-stu-id="89023-103">How to: Use Special Characters in XAML</span></span>
<span data-ttu-id="89023-104">Visual Studio 'da oluşturulan biçimlendirme dosyaları Unicode UTF-8 dosya biçiminde otomatik olarak kaydedilir, bu da vurgu işaretleri gibi çok sayıda özel karakterin doğru kodlandığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="89023-104">Markup files that are created in Visual Studio are automatically saved in the Unicode UTF-8 file format, which means that most special characters, such as accent marks, are encoded correctly.</span></span> <span data-ttu-id="89023-105">Ancak, farklı şekilde işlenen yaygın olarak kullanılan özel karakterlerin bir kümesi vardır.</span><span class="sxs-lookup"><span data-stu-id="89023-105">However, there is a set of commonly-used special characters that are handled differently.</span></span> <span data-ttu-id="89023-106">Bu özel karakterler, kodlama için World Wide Web Konsorsiyumu (W3C) XML standardını izler.</span><span class="sxs-lookup"><span data-stu-id="89023-106">These special characters follow the World Wide Web Consortium (W3C) XML standard for encoding.</span></span>  
  
 <span data-ttu-id="89023-107">Aşağıdaki tabloda, bu özel karakter kümesini kodlamaya yönelik sözdizimi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="89023-107">The following table shows the syntax for encoding this set of special characters:</span></span>  
  
|<span data-ttu-id="89023-108">Karakter</span><span class="sxs-lookup"><span data-stu-id="89023-108">Character</span></span>|<span data-ttu-id="89023-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="89023-109">Syntax</span></span>|<span data-ttu-id="89023-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89023-110">Description</span></span>|  
|---------------|------------|-----------------|  
|<|`&lt;`|<span data-ttu-id="89023-111">Küçüktür simgesi.</span><span class="sxs-lookup"><span data-stu-id="89023-111">Less than symbol.</span></span>|  
|>|`&gt;`|<span data-ttu-id="89023-112">Büyüktür işareti.</span><span class="sxs-lookup"><span data-stu-id="89023-112">Greater than sign.</span></span>|  
|&|`&amp;`|<span data-ttu-id="89023-113">Ve simgesi.</span><span class="sxs-lookup"><span data-stu-id="89023-113">Ampersand symbol.</span></span>|  
|<span data-ttu-id="89023-114">"</span><span class="sxs-lookup"><span data-stu-id="89023-114">"</span></span>|`&quot;`|<span data-ttu-id="89023-115">Çift tırnak simgesi.</span><span class="sxs-lookup"><span data-stu-id="89023-115">Double quote symbol.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="89023-116">Windows Not Defteri gibi bir metin düzenleyicisi kullanarak bir biçimlendirme dosyası oluşturursanız, kodlanmış özel karakterleri korumak için dosyayı Unicode UTF-8 dosya biçiminde kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="89023-116">If you create a markup file using a text editor, such as Windows Notepad, you must save the file in the Unicode UTF-8 file format in order to preserve any encoded special characters.</span></span>  
  
 <span data-ttu-id="89023-117">Aşağıdaki örnek, biçimlendirme oluştururken metindeki özel karakterleri nasıl kullanabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="89023-117">The following example shows how you can use special characters in text when creating markup.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89023-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="89023-118">Example</span></span>  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
