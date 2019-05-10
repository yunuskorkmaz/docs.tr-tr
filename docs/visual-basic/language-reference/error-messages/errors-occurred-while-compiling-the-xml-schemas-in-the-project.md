---
title: Projedeki XML şemaları derlenirken hataları oluştu
ms.date: 07/20/2015
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
ms.openlocfilehash: 7c05c712bcbb0a61bb3121bb71a7823a1c29afb5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625580"
---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a><span data-ttu-id="cef7e-102">Projedeki XML şemaları derlenirken hataları oluştu</span><span class="sxs-lookup"><span data-stu-id="cef7e-102">Errors occurred while compiling the XML schemas in the project</span></span>
<span data-ttu-id="cef7e-103">Projedeki XML şemaları derlenirken hataları oluştu.</span><span class="sxs-lookup"><span data-stu-id="cef7e-103">Errors occurred while compiling the XML schemas in the project.</span></span> <span data-ttu-id="cef7e-104">Bu nedenle, XML IntelliSense kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="cef7e-104">Because of this, XML IntelliSense is not available.</span></span>  
  
 <span data-ttu-id="cef7e-105">Projeye dahil bir XML şema tanımı (XSD) şemasında bir hata var.</span><span class="sxs-lookup"><span data-stu-id="cef7e-105">There is an error in an XML Schema Definition (XSD) schema included in the project.</span></span> <span data-ttu-id="cef7e-106">Proje için mevcut bir XSD şeması ile çakışıyor ayarlanan XSD şema (.xsd) dosyası eklediğinizde, bu hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="cef7e-106">This error occurs when you add an XSD schema (.xsd) file that conflicts with the existing XSD schema set for the project.</span></span>  
  
 <span data-ttu-id="cef7e-107">**Hata Kimliği:** BC36810</span><span class="sxs-lookup"><span data-stu-id="cef7e-107">**Error ID:** BC36810</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cef7e-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="cef7e-108">To correct this error</span></span>  
  
- <span data-ttu-id="cef7e-109">Uyarıyı çift tıklatın **hata listesine** penceresi.</span><span class="sxs-lookup"><span data-stu-id="cef7e-109">Double-click the warning in the **Errors List** window.</span></span> <span data-ttu-id="cef7e-110">Visual Basic uyarısı kaynağı XSD dosyası konumu yönlendirilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cef7e-110">Visual Basic will take you to the location in the XSD file that is the source of the warning.</span></span> <span data-ttu-id="cef7e-111">XSD şema hatasını düzeltin.</span><span class="sxs-lookup"><span data-stu-id="cef7e-111">Correct the error in the XSD schema.</span></span>  
  
- <span data-ttu-id="cef7e-112">Gerekli tüm XSD şema (.xsd) dosyaları projeye dahil olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="cef7e-112">Ensure that all required XSD schema (.xsd) files are included in the project.</span></span> <span data-ttu-id="cef7e-113">Tıklaymanız gerekebilir **tüm dosyaları göster** üzerinde **proje** , .xsd görmek için menü dosyaları **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="cef7e-113">You may need to click **Show All Files** on the **Project** menu to see your .xsd files in **Solution Explorer**.</span></span> <span data-ttu-id="cef7e-114">.Xsd dosyasını sağ tıklatın ve ardından **projeye dahil et** dosyası projenize eklenecek.</span><span class="sxs-lookup"><span data-stu-id="cef7e-114">Right-click an .xsd file and then click **Include In Project** to include the file in your project.</span></span>  
  
- <span data-ttu-id="cef7e-115">XML ve şema Sihirbazı kullanıyorsanız, aynı kaynaktan birden fazla kez şemaları Infer, bu hata oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="cef7e-115">If you are using the XML to Schema Wizard, this error can occur if you infer schemas more than one time from the same source.</span></span> <span data-ttu-id="cef7e-116">Bu durumda, projeden varolan XSD şema dosyalarını kaldırabilirsiniz ekleme yeni bir XML şema öğesi şablonuna ve projeniz için sonra XML şema Sihirbazı ile tüm geçerli XML kaynakları sağlayın.</span><span class="sxs-lookup"><span data-stu-id="cef7e-116">In this case, you can remove the existing XSD schema files from the project, add a new XML to Schema item template, and then provide the XML to Schema Wizard with all the applicable XML sources for your project.</span></span>  
  
- <span data-ttu-id="cef7e-117">XSD Şemanızda herhangi bir hata belirlenirse, ayrıntılı hata iletisi sağlamak için yeterli bilgi XML derleyici olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="cef7e-117">If no error is identified in your XSD schema, the XML compiler may not have enough information to provide a detailed error message.</span></span> <span data-ttu-id="cef7e-118">.Xsd dosyaları için XML ad alanları, proje eşlemesinde Visual Studio'da ayarlamak için XML şeması için belirtilen XML ad alanlarını dahil olun, ayrıntılı hata bilgisini almak mümkün olabilir.</span><span class="sxs-lookup"><span data-stu-id="cef7e-118">You may be able to get more detailed error information if you ensure that the XML namespaces for the .xsd files included in your project match the XML namespaces identified for the XML Schema set in Visual Studio.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cef7e-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cef7e-119">See also</span></span>

- [<span data-ttu-id="cef7e-120">Hata Listesi Penceresi</span><span class="sxs-lookup"><span data-stu-id="cef7e-120">Error List Window</span></span>](/visualstudio/ide/reference/error-list-window)
- [<span data-ttu-id="cef7e-121">XML</span><span class="sxs-lookup"><span data-stu-id="cef7e-121">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
