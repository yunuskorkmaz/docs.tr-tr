---
title: 'Nasıl Yapılır: Tasarım Zamanında Yeni Ayar Oluşturma'
description: Visual Studio 'daki ayarlar tasarımcısını kullanarak tasarım zamanında yeni bir Windows Forms ayarı oluşturmayı öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], design time
- application settings [Windows Forms], creating
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
ms.openlocfilehash: ce37b42191999e29de2f2f7f7e7abfa0ec3f4d47
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325839"
---
# <a name="how-to-create-a-new-setting-at-design-time"></a><span data-ttu-id="84f02-103">Nasıl yapılır: tasarım zamanında yeni ayar oluşturma</span><span class="sxs-lookup"><span data-stu-id="84f02-103">How To: Create a new setting at design time</span></span>

<span data-ttu-id="84f02-104">Tasarım zamanında, Visual Studio 'daki ayarlar tasarımcısını kullanarak yeni bir ayar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84f02-104">You can create a new setting at design time by using the Settings designer in Visual Studio.</span></span> <span data-ttu-id="84f02-105">Ayarlar Tasarımcısı, yeni ayarlar oluşturmanıza ve bu ayarlar için özellikleri belirtmenize olanak tanıyan bir kılavuz stili arabirimdir.</span><span class="sxs-lookup"><span data-stu-id="84f02-105">The Settings designer is a grid-style interface that allows you to create new settings and specify properties for those settings.</span></span> <span data-ttu-id="84f02-106">Yeni ayarlarınız için ad, değer, tür ve kapsam belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="84f02-106">You must specify Name, Value, Type and Scope for your new settings.</span></span> <span data-ttu-id="84f02-107">Bir ayar oluşturulduktan sonra koddan erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="84f02-107">Once a setting is created, it is accessible in code.</span></span>

## <a name="create-a-new-setting-at-design-time-in-c"></a><span data-ttu-id="84f02-108">C 'de tasarım zamanında yeni bir ayar oluşturun\#</span><span class="sxs-lookup"><span data-stu-id="84f02-108">Create a new setting at design time in C\#</span></span>

1. <span data-ttu-id="84f02-109">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="84f02-109">Open Visual Studio.</span></span>

2. <span data-ttu-id="84f02-110">**Çözüm Gezgini**, projenizin **Özellikler** düğümünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="84f02-110">In **Solution Explorer**, expand the **Properties** node of your project.</span></span>

3. <span data-ttu-id="84f02-111">Yeni bir ayar eklemek istediğiniz. Settings dosyasına çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="84f02-111">Double-click the .settings file in which you want to add a new setting.</span></span> <span data-ttu-id="84f02-112">Bu dosya için varsayılan ad Settings. Settings ' dir.</span><span class="sxs-lookup"><span data-stu-id="84f02-112">The default name for this file is Settings.settings.</span></span>

4. <span data-ttu-id="84f02-113">Ayarlar tasarımcısında, ayarınız için **adı**, **değeri**, **türü**ve **kapsamı** ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="84f02-113">In the Settings designer, set the **Name**, **Value**, **Type**, and **Scope** for your setting.</span></span> <span data-ttu-id="84f02-114">Her satır tek bir ayarı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="84f02-114">Each row represents a single setting.</span></span>

## <a name="create-a-new-setting-at-design-time-in-visual-basic"></a><span data-ttu-id="84f02-115">Tasarım zamanında Visual Basic yeni bir ayar oluşturun</span><span class="sxs-lookup"><span data-stu-id="84f02-115">Create a new setting at design time in Visual Basic</span></span>

1. <span data-ttu-id="84f02-116">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="84f02-116">Open Visual Studio.</span></span>

2. <span data-ttu-id="84f02-117">**Çözüm Gezgini**, proje düğümüne sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="84f02-117">In **Solution Explorer**, right-click your project node and choose **Properties**.</span></span>

3. <span data-ttu-id="84f02-118">**Özellikler** sayfasında, **Ayarlar** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="84f02-118">In the **Properties** page, select the **Settings** tab.</span></span>

4. <span data-ttu-id="84f02-119">Ayarlar tasarımcısında, ayarınız için **adı**, **değeri**, **türü**ve **kapsamı** ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="84f02-119">In the Settings designer, set the **Name**, **Value**, **Type**, and **Scope** for your setting.</span></span> <span data-ttu-id="84f02-120">Her satır tek bir ayarı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="84f02-120">Each row represents a single setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="84f02-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84f02-121">See also</span></span>

- [<span data-ttu-id="84f02-122">Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="84f02-122">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="84f02-123">Uygulama Ayarlarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="84f02-123">Application Settings Overview</span></span>](application-settings-overview.md)
- [<span data-ttu-id="84f02-124">Nasıl yapılır: Tasarım Zamanında Mevcut Bir Ayarın Değerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="84f02-124">How To: Change the Value of an Existing Setting at Design Time</span></span>](how-to-change-the-value-of-an-existing-setting-at-design-time.md)
