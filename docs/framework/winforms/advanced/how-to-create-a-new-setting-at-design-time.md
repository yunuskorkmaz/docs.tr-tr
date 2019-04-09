---
title: 'Nasıl yapılır: Tasarım Zamanında Yeni Ayar Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], design time
- application settings [Windows Forms], creating
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
ms.openlocfilehash: 03a96298af68579bb2e67299688928dee0f517de
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198588"
---
# <a name="how-to-create-a-new-setting-at-design-time"></a><span data-ttu-id="2bcc0-102">Nasıl yapılır: Tasarım Zamanında Yeni Ayar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2bcc0-102">How To: Create a New Setting at Design Time</span></span>
<span data-ttu-id="2bcc0-103">Ayarlar Tasarımcısı'nı kullanarak, tasarım zamanında yeni ayar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2bcc0-103">You can create a new setting at design time by using the Settings designer.</span></span> <span data-ttu-id="2bcc0-104">Ayarlar Tasarımcısı yeni ayarları oluşturmak ve bu ayarları özelliklerini belirtmek izin veren bir kılavuz stili arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="2bcc0-104">The Settings designer is a grid-style interface that allows you to create new settings and specify properties for those settings.</span></span> <span data-ttu-id="2bcc0-105">Ad, değer, türü ve yeni ayarlarınız için kapsam belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2bcc0-105">You must specify Name, Value, Type and Scope for your new settings.</span></span> <span data-ttu-id="2bcc0-106">Bir ayar oluşturulduktan sonra kod içinde erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="2bcc0-106">Once a setting is created, it is accessible in code.</span></span>  
  
### <a name="to-create-a-new-setting-at-design-time-in-c"></a><span data-ttu-id="2bcc0-107">C'de tasarım zamanında yeni ayar oluşturma\#</span><span class="sxs-lookup"><span data-stu-id="2bcc0-107">To create a new setting at design time in C\#</span></span>
  
1.  <span data-ttu-id="2bcc0-108">İçinde **Çözüm Gezgini**, genişletme **özellikleri** projenizin düğümü.</span><span class="sxs-lookup"><span data-stu-id="2bcc0-108">In **Solution Explorer**, expand the **Properties** node of your project.</span></span>  
  
2.  <span data-ttu-id="2bcc0-109">Yeni bir ayar eklemek istediğiniz .settings dosyasını çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="2bcc0-109">Double-click the .settings file in which you want to add a new setting.</span></span> <span data-ttu-id="2bcc0-110">Settings.settings bu dosya için varsayılan addır.</span><span class="sxs-lookup"><span data-stu-id="2bcc0-110">The default name for this file is Settings.settings.</span></span>  
  
3.  <span data-ttu-id="2bcc0-111">Ayarlar Tasarımcısı'nda, adını, değeri, türü ve ayarınız için kapsamı ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2bcc0-111">In the Settings designer, set the Name, Value, Type, and Scope for your setting.</span></span> <span data-ttu-id="2bcc0-112">Her satırın tek bir ayar temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2bcc0-112">Each row represents a single setting.</span></span>  
  
### <a name="to-create-a-new-setting-at-design-time-in-visual-basic"></a><span data-ttu-id="2bcc0-113">Visual Basic'te tasarım zamanında yeni ayar oluşturma</span><span class="sxs-lookup"><span data-stu-id="2bcc0-113">To create a new setting at design time in Visual Basic</span></span>  
  
1.  <span data-ttu-id="2bcc0-114">İçinde **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve seçin **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="2bcc0-114">In **Solution Explorer**, right-click your project node and choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="2bcc0-115">İçinde **özellikleri** sayfasında **ayarları** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="2bcc0-115">In the **Properties** page, select the **Settings** tab.</span></span>  
  
3.  <span data-ttu-id="2bcc0-116">Ayarlar Tasarımcısı'nda, adını, değeri, türü ve ayarınız için kapsamı ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2bcc0-116">In the Settings designer, set the Name, Value, Type, and Scope for your setting.</span></span> <span data-ttu-id="2bcc0-117">Her satırın tek bir ayar temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2bcc0-117">Each row represents a single setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bcc0-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2bcc0-118">See also</span></span>

- [<span data-ttu-id="2bcc0-119">Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="2bcc0-119">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="2bcc0-120">Uygulama Ayarlarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2bcc0-120">Application Settings Overview</span></span>](application-settings-overview.md)
- [<span data-ttu-id="2bcc0-121">Nasıl yapılır: Tasarım Zamanında Mevcut Bir Ayarın Değerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="2bcc0-121">How To: Change the Value of an Existing Setting at Design Time</span></span>](how-to-change-the-value-of-an-existing-setting-at-design-time.md)
