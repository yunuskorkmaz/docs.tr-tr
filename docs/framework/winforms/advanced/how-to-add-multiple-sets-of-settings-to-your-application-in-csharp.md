---
title: 'Nasıl yapılır: Uygulamanızda birden çok ayar kümesi eklemeC#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
ms.openlocfilehash: 5496d370890e019ae2b31835c95a9988f8d9bc18
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559417"
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a><span data-ttu-id="738ec-102">Nasıl yapılır: Uygulamanızda birden çok ayar kümesi eklemeC#</span><span class="sxs-lookup"><span data-stu-id="738ec-102">How To: Add Multiple Sets of Settings To Your Application in C#</span></span> #
<span data-ttu-id="738ec-103">Bazı durumlarda, bir uygulamada birden çok ayar kümesi olmasını isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="738ec-103">In some cases, you might want to have multiple sets of settings in an application.</span></span> <span data-ttu-id="738ec-104">Burada belirli bir grubun ayarlarının sık değiştirilmesi beklenmeyen bir uygulama geliştiriyorsanız, örneğin, Etkilenmeyen diğer ayarları değiştirmeden böylece dosyayı tümden değiştirilebilir tümü tek bir dosyaya ayırarak akıllıca olabilir.</span><span class="sxs-lookup"><span data-stu-id="738ec-104">For example, if you are developing an application where a particular group of settings is expected to change frequently, it might be wise to separate them all into a single file so that the file can be replaced wholesale, leaving other settings unaffected.</span></span> <span data-ttu-id="738ec-105">Visual Studio projenize birden çok ayar kümesi eklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="738ec-105">Visual Studio allows you to add multiple sets of settings to your project.</span></span> <span data-ttu-id="738ec-106">Ek ayarları kümesi Properties.Settings nesnesi erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="738ec-106">Additional sets of settings can be accessed via the Properties.Settings object.</span></span>  
  
### <a name="to-add-an-additional-set-of-setting-to-your-application"></a><span data-ttu-id="738ec-107">Uygulamanıza ek bir ayar kümesi eklemek için</span><span class="sxs-lookup"><span data-stu-id="738ec-107">To Add an Additional Set of Setting to your Application</span></span>  
  
1.  <span data-ttu-id="738ec-108">Gelen **proje** menüsünde seçin **Yeni Öğe Ekle**.</span><span class="sxs-lookup"><span data-stu-id="738ec-108">From the **Project** menu, choose **Add New Item**.</span></span> <span data-ttu-id="738ec-109">**Yeni Öğe Ekle** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="738ec-109">The **Add New Item** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="738ec-110">İçinde **Yeni Öğe Ekle** iletişim kutusunda **ayarları dosyası**, dosya için bir ad yazın ve tıklayın **Ekle** çözümünüze yeni bir ayarlar dosyası eklemek için.</span><span class="sxs-lookup"><span data-stu-id="738ec-110">In the **Add New Item** dialog box, select **Settings File**, type in a name for the file, and click **Add** to add a new settings file to your solution.</span></span>  
  
3.  <span data-ttu-id="738ec-111">İçinde **Çözüm Gezgini**, yeni ayarları dosyasına sürükleyin **özellikleri** klasör.</span><span class="sxs-lookup"><span data-stu-id="738ec-111">In **Solution Explorer**, drag the new Settings file into the **Properties** folder.</span></span> <span data-ttu-id="738ec-112">Bu yeni ayarlarınızı kodda kullanılabilir olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="738ec-112">This allows your new settings to be available in code.</span></span>  
  
4.  <span data-ttu-id="738ec-113">Ekleme ve diğer ayarları dosyası gibi bu dosyada ayarları kullanın.</span><span class="sxs-lookup"><span data-stu-id="738ec-113">Add and use settings in this file as you would any other settings file.</span></span> <span data-ttu-id="738ec-114">Bu Grup ayarlarını Properties.Settings nesnesi aracılığıyla erişebilir.</span><span class="sxs-lookup"><span data-stu-id="738ec-114">You can access this group of settings via the Properties.Settings object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="738ec-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="738ec-115">See also</span></span>
- [<span data-ttu-id="738ec-116">Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="738ec-116">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)
- [<span data-ttu-id="738ec-117">Uygulama Ayarlarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="738ec-117">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
