---
title: 'Son değişiklik: PublishDepsFilePath davranış değişikliği'
description: .NET 5,0 'de, tek dosya uygulamaları için PublishDepsFilePath MSBuild özelliğinin boş olduğu son değişiklik hakkında bilgi edinin.
ms.date: 09/17/2020
ms.openlocfilehash: 70631beff31aa3388e59f3b79875ef437351451a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761735"
---
# <a name="publishdepsfilepath-behavior-change"></a><span data-ttu-id="e4fbb-103">PublishDepsFilePath davranış değişikliği</span><span class="sxs-lookup"><span data-stu-id="e4fbb-103">PublishDepsFilePath behavior change</span></span>

<span data-ttu-id="e4fbb-104">`PublishDepsFilePath`MSBuild özelliği, tek dosya uygulamaları için boştur.</span><span class="sxs-lookup"><span data-stu-id="e4fbb-104">The `PublishDepsFilePath` MSBuild property is empty for single-file applications.</span></span> <span data-ttu-id="e4fbb-105">Ayrıca, tek dosya olmayan uygulamalar için, dosya *deps.js* , derleme içinde daha sonra çıkış dizinine kopyalanamayabilir.</span><span class="sxs-lookup"><span data-stu-id="e4fbb-105">Additionally, for non single-file applications, the *deps.json* file may not be copied to the output directory until later in the build.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="e4fbb-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="e4fbb-106">Version introduced</span></span>

<span data-ttu-id="e4fbb-107">5.0</span><span class="sxs-lookup"><span data-stu-id="e4fbb-107">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="e4fbb-108">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="e4fbb-108">Change description</span></span>

<span data-ttu-id="e4fbb-109">Önceki .NET sürümlerinde, `PublishDepsFilePath` MSBuild özelliği, tek dosya olmayan uygulamalar için çıkış dizinindeki dosyanın *deps.js* yolu ve tek dosya uygulamalarına yönelik ara dizindeki bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="e4fbb-109">In previous .NET versions, the `PublishDepsFilePath` MSBuild property is the path to the app's *deps.json* file in the output directory for non single-file applications, and a path in the intermediate directory for single-file apps.</span></span>

<span data-ttu-id="e4fbb-110">.NET 5,0 ' den itibaren, `PublishDepsFilePath` tek dosya uygulamaları için boştur ve yeni bir `IntermediateDepsFilePath` özellik ara dizindeki konumdaki *deps.js* belirtir.</span><span class="sxs-lookup"><span data-stu-id="e4fbb-110">Starting in .NET 5.0, `PublishDepsFilePath` is empty for single-file applications and a new `IntermediateDepsFilePath` property specifies the *deps.json* location in the intermediate directory.</span></span> <span data-ttu-id="e4fbb-111">Ayrıca, tek dosya olmayan uygulamalar için, dosyadaki *deps.js* , `PublishDepsFilePath` derleme içinde daha sonra olana kadar çıkış dizinine (yani, tarafından belirtilen yol) kopyalanmayabilir.</span><span class="sxs-lookup"><span data-stu-id="e4fbb-111">Additionally, for non single-file applications, the *deps.json* file may not be copied to the output directory (that is, the path specified by `PublishDepsFilePath`) until later in the build.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="e4fbb-112">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="e4fbb-112">Reason for change</span></span>

<span data-ttu-id="e4fbb-113">Bu değişiklik birkaç nedenden dolayı yapıldı:</span><span class="sxs-lookup"><span data-stu-id="e4fbb-113">This change was made for a couple of reasons:</span></span>

- <span data-ttu-id="e4fbb-114">.NET 5 ' te [geliştirilmiş tek dosya uygulamalarını](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md) desteklemek için yayımlama mantığının yeniden düzenlenmesi nedeniyle.</span><span class="sxs-lookup"><span data-stu-id="e4fbb-114">Due to a refactoring of the publish logic in order to support [improved single-file apps](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md) in .NET 5.</span></span>

- <span data-ttu-id="e4fbb-115">Tek dosya uygulamalarında, *deps.json* önceden paketlenmiş olduktan sonra dosyayı *deps.js* yeniden yazmayı deneyen hedeflere karşı koruma sağlamaya yardımcı olmak için, uygulamayı sessizce etkilememelidir.</span><span class="sxs-lookup"><span data-stu-id="e4fbb-115">In single-file apps, to help guard against targets that try to rewrite the *deps.json* file after *deps.json* has already been bundled, thus silently not affecting the app.</span></span> <span data-ttu-id="e4fbb-116">Bu nedenle, `PublishDepsFilePath` tek dosya uygulamaları için boştur.</span><span class="sxs-lookup"><span data-stu-id="e4fbb-116">For this reason, `PublishDepsFilePath` is empty for single-file applications.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="e4fbb-117">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="e4fbb-117">Recommended action</span></span>

<span data-ttu-id="e4fbb-118">Dosyayı *deps.js* yeniden yazan hedefler genellikle özelliğini kullanarak bunu yapmanız gerekir `IntermediateDepsFilePath` .</span><span class="sxs-lookup"><span data-stu-id="e4fbb-118">Targets that rewrite the *deps.json* file should generally do so using the `IntermediateDepsFilePath` property.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="e4fbb-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="e4fbb-119">Affected APIs</span></span>

<span data-ttu-id="e4fbb-120">YOK</span><span class="sxs-lookup"><span data-stu-id="e4fbb-120">N/A</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

MSBuild

-->
