---
ms.openlocfilehash: 9659068304eb208fd6a0a753273453bc669fbc56
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621405"
---
### <a name="keytips-behavior-improved-in-wpf"></a><span data-ttu-id="d2c4c-101">WPF 'de geliştirilmiş KeyTips davranışı</span><span class="sxs-lookup"><span data-stu-id="d2c4c-101">Keytips behavior improved in WPF</span></span>

#### <a name="details"></a><span data-ttu-id="d2c4c-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="d2c4c-102">Details</span></span>

<span data-ttu-id="d2c4c-103">KeyTips davranışı, Microsoft Word ve Windows Gezgini 'ndeki davranışa eşlik eden şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d2c4c-103">Keytips behavior has been modified to bring parity with behavior on Microsoft Word and Windows Explorer.</span></span> <span data-ttu-id="d2c4c-104">Anahtar ipucu durumunun etkin olup olmadığını kontrol ederek <xref:System.Windows.Input.KeyEventArgs.SystemKey> (özellikle <xref:System.Windows.Input.Key> veya <xref:System.Windows.Input.Key.F11> ) basıldığında, WPF KeyTip tuşlarını uygun şekilde işler.</span><span class="sxs-lookup"><span data-stu-id="d2c4c-104">By checking whether keytip state is enabled or not in the case of a <xref:System.Windows.Input.KeyEventArgs.SystemKey> (in particular, <xref:System.Windows.Input.Key> or <xref:System.Windows.Input.Key.F11>) being pressed, WPF handles keytip keys appropriately.</span></span> <span data-ttu-id="d2c4c-105">KeyTips artık fare tarafından açılsa bile menüyü kapatabilir.</span><span class="sxs-lookup"><span data-stu-id="d2c4c-105">Keytips now dismiss a menu even when it is opened by mouse.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d2c4c-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="d2c4c-106">Suggestion</span></span>

<span data-ttu-id="d2c4c-107">Yok</span><span class="sxs-lookup"><span data-stu-id="d2c4c-107">N/A</span></span>

| <span data-ttu-id="d2c4c-108">Name</span><span class="sxs-lookup"><span data-stu-id="d2c4c-108">Name</span></span>    | <span data-ttu-id="d2c4c-109">Değer</span><span class="sxs-lookup"><span data-stu-id="d2c4c-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d2c4c-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="d2c4c-110">Scope</span></span>   |<span data-ttu-id="d2c4c-111">Edge</span><span class="sxs-lookup"><span data-stu-id="d2c4c-111">Edge</span></span>|
|<span data-ttu-id="d2c4c-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="d2c4c-112">Version</span></span>|<span data-ttu-id="d2c4c-113">4.7.2</span><span class="sxs-lookup"><span data-stu-id="d2c4c-113">4.7.2</span></span>|
|<span data-ttu-id="d2c4c-114">Tür</span><span class="sxs-lookup"><span data-stu-id="d2c4c-114">Type</span></span>|<span data-ttu-id="d2c4c-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="d2c4c-115">Runtime</span></span>|
