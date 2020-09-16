---
ms.openlocfilehash: 077eadb05ab16f5cec8817b89bc771de0c94aefa
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679347"
---
### <a name="publishdepsfilepath-behavior-change"></a><span data-ttu-id="e21a1-101">PublishDepsFilePath davranış değişikliği</span><span class="sxs-lookup"><span data-stu-id="e21a1-101">PublishDepsFilePath behavior change</span></span>

<span data-ttu-id="e21a1-102">`PublishDepsFilePath`MSBuild özelliği, tek dosya uygulamaları için boştur.</span><span class="sxs-lookup"><span data-stu-id="e21a1-102">The `PublishDepsFilePath` MSBuild property is empty for single-file applications.</span></span> <span data-ttu-id="e21a1-103">Ayrıca, tek dosya olmayan uygulamalar için, dosya *deps.js* , derleme içinde daha sonra çıkış dizinine kopyalanamayabilir.</span><span class="sxs-lookup"><span data-stu-id="e21a1-103">Additionally, for non single-file applications, the *deps.json* file may not be copied to the output directory until later in the build.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e21a1-104">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="e21a1-104">Version introduced</span></span>

<span data-ttu-id="e21a1-105">5.0</span><span class="sxs-lookup"><span data-stu-id="e21a1-105">5.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="e21a1-106">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="e21a1-106">Change description</span></span>

<span data-ttu-id="e21a1-107">Önceki .NET sürümlerinde, `PublishDepsFilePath` MSBuild özelliği, tek dosya olmayan uygulamalar için çıkış dizinindeki dosyanın *deps.js* yolu ve tek dosya uygulamalarına yönelik ara dizindeki bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="e21a1-107">In previous .NET versions, the `PublishDepsFilePath` MSBuild property is the path to the app's *deps.json* file in the output directory for non single-file applications, and a path in the intermediate directory for single-file apps.</span></span>

<span data-ttu-id="e21a1-108">.NET 5,0 ' den itibaren, `PublishDepsFilePath` tek dosya uygulamaları için boştur ve yeni bir `IntermediateDepsFilePath` özellik ara dizindeki konumdaki *deps.js* belirtir.</span><span class="sxs-lookup"><span data-stu-id="e21a1-108">Starting in .NET 5.0, `PublishDepsFilePath` is empty for single-file applications and a new `IntermediateDepsFilePath` property specifies the *deps.json* location in the intermediate directory.</span></span> <span data-ttu-id="e21a1-109">Ayrıca, tek dosya olmayan uygulamalar için, dosyadaki *deps.js* , `PublishDepsFilePath` derleme içinde daha sonra olana kadar çıkış dizinine (yani, tarafından belirtilen yol) kopyalanmayabilir.</span><span class="sxs-lookup"><span data-stu-id="e21a1-109">Additionally, for non single-file applications, the *deps.json* file may not be copied to the output directory (that is, the path specified by `PublishDepsFilePath`) until later in the build.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e21a1-110">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="e21a1-110">Reason for change</span></span>

<span data-ttu-id="e21a1-111">Bu değişiklik birkaç nedenden dolayı yapıldı:</span><span class="sxs-lookup"><span data-stu-id="e21a1-111">This change was made for a couple of reasons:</span></span>

- <span data-ttu-id="e21a1-112">.NET 5 ' te [geliştirilmiş tek dosya uygulamalarını](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md) desteklemek için yayımlama mantığının yeniden düzenlenmesi nedeniyle.</span><span class="sxs-lookup"><span data-stu-id="e21a1-112">Due to a refactoring of the publish logic in order to support [improved single-file apps](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md) in .NET 5.</span></span>

- <span data-ttu-id="e21a1-113">Tek dosya uygulamalarında, *deps.json* önceden paketlenmiş olduktan sonra dosyayı *deps.js* yeniden yazmayı deneyen hedeflere karşı koruma sağlamaya yardımcı olmak için, uygulamayı sessizce etkilememelidir.</span><span class="sxs-lookup"><span data-stu-id="e21a1-113">In single-file apps, to help guard against targets that try to rewrite the *deps.json* file after *deps.json* has already been bundled, thus silently not affecting the app.</span></span> <span data-ttu-id="e21a1-114">Bu nedenle, `PublishDepsFilePath` tek dosya uygulamaları için boştur.</span><span class="sxs-lookup"><span data-stu-id="e21a1-114">For this reason, `PublishDepsFilePath` is empty for single-file applications.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e21a1-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="e21a1-115">Recommended action</span></span>

<span data-ttu-id="e21a1-116">Dosyayı *deps.js* yeniden yazan hedefler genellikle özelliğini kullanarak bunu yapmanız gerekir `IntermediateDepsFilePath` .</span><span class="sxs-lookup"><span data-stu-id="e21a1-116">Targets that rewrite the *deps.json* file should generally do so using the `IntermediateDepsFilePath` property.</span></span>

#### <a name="category"></a><span data-ttu-id="e21a1-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="e21a1-117">Category</span></span>

<span data-ttu-id="e21a1-118">MSBuild</span><span class="sxs-lookup"><span data-stu-id="e21a1-118">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e21a1-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="e21a1-119">Affected APIs</span></span>

<span data-ttu-id="e21a1-120">Yok</span><span class="sxs-lookup"><span data-stu-id="e21a1-120">N/A</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
