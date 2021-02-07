---
description: 'Hakkında daha fazla bilgi edinin: 1004-Workflowınstancedurdurulan'
title: 1004 - WorkflowInstanceAborted
ms.date: 03/30/2017
ms.assetid: edb9ab8c-0b9a-488d-aa96-9c8c7984b53c
ms.openlocfilehash: 4aaa0899da9b0b8510684a13537a8cb8f9117ee1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755634"
---
# <a name="1004---workflowinstanceaborted"></a><span data-ttu-id="31764-103">1004 - WorkflowInstanceAborted</span><span class="sxs-lookup"><span data-stu-id="31764-103">1004 - WorkflowInstanceAborted</span></span>

## <a name="properties"></a><span data-ttu-id="31764-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="31764-104">Properties</span></span>

|||
|-|-|
|<span data-ttu-id="31764-105">ID</span><span class="sxs-lookup"><span data-stu-id="31764-105">ID</span></span>|<span data-ttu-id="31764-106">1004</span><span class="sxs-lookup"><span data-stu-id="31764-106">1004</span></span>|
|<span data-ttu-id="31764-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="31764-107">Keywords</span></span>|<span data-ttu-id="31764-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="31764-108">WFRuntime</span></span>|
|<span data-ttu-id="31764-109">Level</span><span class="sxs-lookup"><span data-stu-id="31764-109">Level</span></span>|<span data-ttu-id="31764-110">Bilgi</span><span class="sxs-lookup"><span data-stu-id="31764-110">Information</span></span>|
|<span data-ttu-id="31764-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="31764-111">Channel</span></span>|<span data-ttu-id="31764-112">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="31764-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|

## <a name="description"></a><span data-ttu-id="31764-113">Description</span><span class="sxs-lookup"><span data-stu-id="31764-113">Description</span></span>

<span data-ttu-id="31764-114">Bir iş akışı örneğinin bir özel durumla durdurulduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="31764-114">Indicates a workflow instance has aborted with an exception.</span></span>

## <a name="message"></a><span data-ttu-id="31764-115">İleti</span><span class="sxs-lookup"><span data-stu-id="31764-115">Message</span></span>

<span data-ttu-id="31764-116">WorkflowInstance kimliği: ' %1 ' bir özel durumla durduruldu.</span><span class="sxs-lookup"><span data-stu-id="31764-116">WorkflowInstance Id: '%1' was aborted with an exception.</span></span>

## <a name="details"></a><span data-ttu-id="31764-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="31764-117">Details</span></span>

|<span data-ttu-id="31764-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="31764-118">Data Item Name</span></span>|<span data-ttu-id="31764-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="31764-119">Data Item Type</span></span>|<span data-ttu-id="31764-120">Description</span><span class="sxs-lookup"><span data-stu-id="31764-120">Description</span></span>|
|--------------------|--------------------|-----------------|
|<span data-ttu-id="31764-121">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="31764-121">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="31764-122">İş akışının örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="31764-122">The instance id for the workflow</span></span>|
|<span data-ttu-id="31764-123">Özel durum</span><span class="sxs-lookup"><span data-stu-id="31764-123">Exception</span></span>|`xs:string`|<span data-ttu-id="31764-124">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="31764-124">The exception details for the exception</span></span>|
|<span data-ttu-id="31764-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="31764-125">AppDomain</span></span>|`xs:string`|<span data-ttu-id="31764-126">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="31764-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
