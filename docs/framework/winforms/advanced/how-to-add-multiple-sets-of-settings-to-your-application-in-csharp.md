---
title: "Nasıl yapılır: Uygulamanıza C#'de Birden Çok Ayar Kümesi Ekleme"
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
ms.openlocfilehash: c6842d11c04e905d42734af939f2c3f0cfeacd47
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040119"
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a><span data-ttu-id="42842-102">Nasıl yapılır: C 'de uygulamanıza birden çok ayar kümesi ekleme\#</span><span class="sxs-lookup"><span data-stu-id="42842-102">How To: Add Multiple Sets of Settings To Your Application in C\#</span></span>

<span data-ttu-id="42842-103">Bazı durumlarda, bir uygulamada birden fazla ayar kümesine sahip olmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42842-103">In some cases, you might want to have multiple sets of settings in an application.</span></span> <span data-ttu-id="42842-104">Örneğin, belirli bir ayar grubunun sıklıkla değiştirilmesi beklenen bir uygulama geliştiriyorsanız, dosyanın toplu olarak değiştirilebilmesi ve diğer ayarların etkilenmemesi için tümünü tek bir dosya halinde ayırmak sizin için gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="42842-104">For example, if you are developing an application where a particular group of settings is expected to change frequently, it might be wise to separate them all into a single file so that the file can be replaced wholesale, leaving other settings unaffected.</span></span> <span data-ttu-id="42842-105">Visual Studio, projenize birden çok ayar kümesi eklemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="42842-105">Visual Studio allows you to add multiple sets of settings to your project.</span></span> <span data-ttu-id="42842-106">`Properties.Settings` Nesne aracılığıyla ek ayar kümelerine erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="42842-106">Additional sets of settings can be accessed via the `Properties.Settings` object.</span></span>

## <a name="add-an-additional-set-of-settings"></a><span data-ttu-id="42842-107">Ek ayar kümesi ekleme</span><span class="sxs-lookup"><span data-stu-id="42842-107">Add an Additional Set of Settings</span></span>

1. <span data-ttu-id="42842-108">Visual Studio 'da, **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="42842-108">In Visual Studio, from the **Project** menu, choose **Add New Item**.</span></span>

   <span data-ttu-id="42842-109">**Yeni Öğe Ekle** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="42842-109">The **Add New Item** dialog box opens.</span></span>

2. <span data-ttu-id="42842-110">**Yeni öğe Ekle** iletişim kutusunda, **ayarlar dosyası**' nı seçin, dosya için bir ad girin ve çözümünüze yeni bir ayarlar dosyası eklemek için **Ekle** ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="42842-110">In the **Add New Item** dialog box, select **Settings File**, enter a name for the file, and click **Add** to add a new settings file to your solution.</span></span>

3. <span data-ttu-id="42842-111">**Çözüm Gezgini**, yeni ayarlar dosyasını **Özellikler** klasörüne sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="42842-111">In **Solution Explorer**, drag the new Settings file into the **Properties** folder.</span></span> <span data-ttu-id="42842-112">Bu, yeni ayarlarınızın kodda kullanılabilir olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="42842-112">This allows your new settings to be available in code.</span></span>

4. <span data-ttu-id="42842-113">Diğer ayarlar dosyası gibi bu dosyadaki ayarları ekleyin ve kullanın.</span><span class="sxs-lookup"><span data-stu-id="42842-113">Add and use settings in this file as you would any other settings file.</span></span> <span data-ttu-id="42842-114">Bu ayar grubuna `Properties.Settings` nesne aracılığıyla erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42842-114">You can access this group of settings via the `Properties.Settings` object.</span></span>

## <a name="see-also"></a><span data-ttu-id="42842-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42842-115">See also</span></span>

- [<span data-ttu-id="42842-116">Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="42842-116">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="42842-117">Uygulama Ayarlarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="42842-117">Application Settings Overview</span></span>](application-settings-overview.md)
