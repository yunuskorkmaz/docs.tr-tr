---
title: 'Nasıl yapılır: Tasarım Zamanında Yeni Ayar Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], design time
- application settings [Windows Forms], creating
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
ms.openlocfilehash: 35a7cd8cc1daaf76a25977751ddc9ec0709e5947
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037901"
---
# <a name="how-to-create-a-new-setting-at-design-time"></a><span data-ttu-id="a8064-102">Nasıl yapılır: Tasarım zamanında yeni bir ayar oluşturun</span><span class="sxs-lookup"><span data-stu-id="a8064-102">How To: Create a new setting at design time</span></span>

<span data-ttu-id="a8064-103">Tasarım zamanında, Visual Studio 'daki ayarlar tasarımcısını kullanarak yeni bir ayar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8064-103">You can create a new setting at design time by using the Settings designer in Visual Studio.</span></span> <span data-ttu-id="a8064-104">Ayarlar Tasarımcısı, yeni ayarlar oluşturmanıza ve bu ayarlar için özellikleri belirtmenize olanak tanıyan bir kılavuz stili arabirimdir.</span><span class="sxs-lookup"><span data-stu-id="a8064-104">The Settings designer is a grid-style interface that allows you to create new settings and specify properties for those settings.</span></span> <span data-ttu-id="a8064-105">Yeni ayarlarınız için ad, değer, tür ve kapsam belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a8064-105">You must specify Name, Value, Type and Scope for your new settings.</span></span> <span data-ttu-id="a8064-106">Bir ayar oluşturulduktan sonra koddan erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a8064-106">Once a setting is created, it is accessible in code.</span></span>

## <a name="create-a-new-setting-at-design-time-in-c"></a><span data-ttu-id="a8064-107">C 'de tasarım zamanında yeni bir ayar oluşturun\#</span><span class="sxs-lookup"><span data-stu-id="a8064-107">Create a new setting at design time in C\#</span></span>

1. <span data-ttu-id="a8064-108">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="a8064-108">Open Visual Studio.</span></span>

2. <span data-ttu-id="a8064-109">**Çözüm Gezgini**, projenizin **Özellikler** düğümünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="a8064-109">In **Solution Explorer**, expand the **Properties** node of your project.</span></span>

3. <span data-ttu-id="a8064-110">Yeni bir ayar eklemek istediğiniz. Settings dosyasına çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a8064-110">Double-click the .settings file in which you want to add a new setting.</span></span> <span data-ttu-id="a8064-111">Bu dosya için varsayılan ad Settings. Settings ' dir.</span><span class="sxs-lookup"><span data-stu-id="a8064-111">The default name for this file is Settings.settings.</span></span>

4. <span data-ttu-id="a8064-112">Ayarlar tasarımcısında, ayarınız için **adı**, **değeri**, **türü**ve **kapsamı** ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a8064-112">In the Settings designer, set the **Name**, **Value**, **Type**, and **Scope** for your setting.</span></span> <span data-ttu-id="a8064-113">Her satır tek bir ayarı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a8064-113">Each row represents a single setting.</span></span>

## <a name="create-a-new-setting-at-design-time-in-visual-basic"></a><span data-ttu-id="a8064-114">Tasarım zamanında Visual Basic yeni bir ayar oluşturun</span><span class="sxs-lookup"><span data-stu-id="a8064-114">Create a new setting at design time in Visual Basic</span></span>

1. <span data-ttu-id="a8064-115">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="a8064-115">Open Visual Studio.</span></span>

2. <span data-ttu-id="a8064-116">**Çözüm Gezgini**, proje düğümüne sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="a8064-116">In **Solution Explorer**, right-click your project node and choose **Properties**.</span></span>

3. <span data-ttu-id="a8064-117">**Özellikler** sayfasında, **Ayarlar** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="a8064-117">In the **Properties** page, select the **Settings** tab.</span></span>

4. <span data-ttu-id="a8064-118">Ayarlar tasarımcısında, ayarınız için **adı**, **değeri**, **türü**ve **kapsamı** ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a8064-118">In the Settings designer, set the **Name**, **Value**, **Type**, and **Scope** for your setting.</span></span> <span data-ttu-id="a8064-119">Her satır tek bir ayarı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a8064-119">Each row represents a single setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8064-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8064-120">See also</span></span>

- [<span data-ttu-id="a8064-121">Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="a8064-121">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="a8064-122">Uygulama Ayarlarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a8064-122">Application Settings Overview</span></span>](application-settings-overview.md)
- [<span data-ttu-id="a8064-123">Nasıl yapılır: Tasarım zamanında mevcut bir ayarın değerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="a8064-123">How To: Change the Value of an Existing Setting at Design Time</span></span>](how-to-change-the-value-of-an-existing-setting-at-design-time.md)
