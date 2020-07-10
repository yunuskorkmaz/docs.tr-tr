---
title: "Nasıl Yapılır: Uygulamanıza C#'de Birden Çok Ayar Kümesi Ekleme"
description: Visual Studio 'Yu kullanarak C# ' de uygulamanıza birden çok Windows Forms ayarları kümesi eklemeyi öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
ms.openlocfilehash: 579374ff101758b3224bc122c46b891280ed2609
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173451"
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a><span data-ttu-id="4a84e-103">Nasıl yapılır: C 'de uygulamanıza birden çok ayar kümesi ekleme\#</span><span class="sxs-lookup"><span data-stu-id="4a84e-103">How To: Add Multiple Sets of Settings To Your Application in C\#</span></span>

<span data-ttu-id="4a84e-104">Bazı durumlarda, bir uygulamada birden fazla ayar kümesine sahip olmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4a84e-104">In some cases, you might want to have multiple sets of settings in an application.</span></span> <span data-ttu-id="4a84e-105">Örneğin, belirli bir ayar grubunun sıklıkla değiştirilmesi beklenen bir uygulama geliştiriyorsanız, dosyanın toplu olarak değiştirilebilmesi ve diğer ayarların etkilenmemesi için tümünü tek bir dosya halinde ayırmak sizin için gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="4a84e-105">For example, if you are developing an application where a particular group of settings is expected to change frequently, it might be wise to separate them all into a single file so that the file can be replaced wholesale, leaving other settings unaffected.</span></span> <span data-ttu-id="4a84e-106">Visual Studio, projenize birden çok ayar kümesi eklemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="4a84e-106">Visual Studio allows you to add multiple sets of settings to your project.</span></span> <span data-ttu-id="4a84e-107">Nesne aracılığıyla ek ayar kümelerine erişilebilir `Properties.Settings` .</span><span class="sxs-lookup"><span data-stu-id="4a84e-107">Additional sets of settings can be accessed via the `Properties.Settings` object.</span></span>

## <a name="add-an-additional-set-of-settings"></a><span data-ttu-id="4a84e-108">Ek ayar kümesi ekleme</span><span class="sxs-lookup"><span data-stu-id="4a84e-108">Add an Additional Set of Settings</span></span>

1. <span data-ttu-id="4a84e-109">Visual Studio 'da, **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="4a84e-109">In Visual Studio, from the **Project** menu, choose **Add New Item**.</span></span>

   <span data-ttu-id="4a84e-110">**Yeni öğe Ekle** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="4a84e-110">The **Add New Item** dialog box opens.</span></span>

2. <span data-ttu-id="4a84e-111">**Yeni öğe Ekle** iletişim kutusunda, **ayarlar dosyası**' nı seçin, dosya için bir ad girin ve çözümünüze yeni bir ayarlar dosyası eklemek için **Ekle** ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4a84e-111">In the **Add New Item** dialog box, select **Settings File**, enter a name for the file, and click **Add** to add a new settings file to your solution.</span></span>

3. <span data-ttu-id="4a84e-112">**Çözüm Gezgini**, yeni ayarlar dosyasını **Özellikler** klasörüne sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="4a84e-112">In **Solution Explorer**, drag the new Settings file into the **Properties** folder.</span></span> <span data-ttu-id="4a84e-113">Bu, yeni ayarlarınızın kodda kullanılabilir olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="4a84e-113">This allows your new settings to be available in code.</span></span>

4. <span data-ttu-id="4a84e-114">Diğer ayarlar dosyası gibi bu dosyadaki ayarları ekleyin ve kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a84e-114">Add and use settings in this file as you would any other settings file.</span></span> <span data-ttu-id="4a84e-115">Bu ayar grubuna nesne aracılığıyla erişebilirsiniz `Properties.Settings` .</span><span class="sxs-lookup"><span data-stu-id="4a84e-115">You can access this group of settings via the `Properties.Settings` object.</span></span>

## <a name="see-also"></a><span data-ttu-id="4a84e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a84e-116">See also</span></span>

- [<span data-ttu-id="4a84e-117">Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="4a84e-117">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="4a84e-118">Uygulama Ayarlarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4a84e-118">Application Settings Overview</span></span>](application-settings-overview.md)
