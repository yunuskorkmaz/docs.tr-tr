---
title: 1004 - WorkflowInstanceAborted
ms.date: 03/30/2017
ms.assetid: edb9ab8c-0b9a-488d-aa96-9c8c7984b53c
ms.openlocfilehash: d34f6f1ab6af8e06a0f28fb043faf9fe16a8b211
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008622"
---
# <a name="1004---workflowinstanceaborted"></a><span data-ttu-id="0af2c-102">1004 - WorkflowInstanceAborted</span><span class="sxs-lookup"><span data-stu-id="0af2c-102">1004 - WorkflowInstanceAborted</span></span>

## <a name="properties"></a><span data-ttu-id="0af2c-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="0af2c-103">Properties</span></span>

|||
|-|-|
|<span data-ttu-id="0af2c-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="0af2c-104">ID</span></span>|<span data-ttu-id="0af2c-105">1004</span><span class="sxs-lookup"><span data-stu-id="0af2c-105">1004</span></span>|
|<span data-ttu-id="0af2c-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="0af2c-106">Keywords</span></span>|<span data-ttu-id="0af2c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="0af2c-107">WFRuntime</span></span>|
|<span data-ttu-id="0af2c-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="0af2c-108">Level</span></span>|<span data-ttu-id="0af2c-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="0af2c-109">Information</span></span>|
|<span data-ttu-id="0af2c-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="0af2c-110">Channel</span></span>|<span data-ttu-id="0af2c-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="0af2c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|

## <a name="description"></a><span data-ttu-id="0af2c-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0af2c-112">Description</span></span>

<span data-ttu-id="0af2c-113">Bir özel durum ile bir iş akışı örneği iptal edildi gösterir.</span><span class="sxs-lookup"><span data-stu-id="0af2c-113">Indicates a workflow instance has aborted with an exception.</span></span>

## <a name="message"></a><span data-ttu-id="0af2c-114">İleti</span><span class="sxs-lookup"><span data-stu-id="0af2c-114">Message</span></span>

<span data-ttu-id="0af2c-115">WorkflowInstance ID: '%1', bir özel durum ile iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="0af2c-115">WorkflowInstance Id: '%1' was aborted with an exception.</span></span>

## <a name="details"></a><span data-ttu-id="0af2c-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="0af2c-116">Details</span></span>

|<span data-ttu-id="0af2c-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="0af2c-117">Data Item Name</span></span>|<span data-ttu-id="0af2c-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="0af2c-118">Data Item Type</span></span>|<span data-ttu-id="0af2c-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0af2c-119">Description</span></span>|
|--------------------|--------------------|-----------------|
|<span data-ttu-id="0af2c-120">WorkflowInstanceID</span><span class="sxs-lookup"><span data-stu-id="0af2c-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="0af2c-121">İş akışı örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="0af2c-121">The instance id for the workflow</span></span>|
|<span data-ttu-id="0af2c-122">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="0af2c-122">Exception</span></span>|`xs:string`|<span data-ttu-id="0af2c-123">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="0af2c-123">The exception details for the exception</span></span>|
|<span data-ttu-id="0af2c-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0af2c-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="0af2c-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="0af2c-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
