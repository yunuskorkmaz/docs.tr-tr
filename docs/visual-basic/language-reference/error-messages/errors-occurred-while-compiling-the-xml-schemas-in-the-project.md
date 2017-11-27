---
title: "Projedeki XML şemaları derlenirken hataları oluştu"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords: BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 07233ed1c68f85878ffdd7131f64e30e158dc350
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a><span data-ttu-id="88cef-102">Projedeki XML şemaları derlenirken hataları oluştu</span><span class="sxs-lookup"><span data-stu-id="88cef-102">Errors occurred while compiling the XML schemas in the project</span></span>
<span data-ttu-id="88cef-103">Projedeki XML şemaları derlenirken hataları oluştu.</span><span class="sxs-lookup"><span data-stu-id="88cef-103">Errors occurred while compiling the XML schemas in the project.</span></span> <span data-ttu-id="88cef-104">Bu nedenle, XML IntelliSense'i kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="88cef-104">Because of this, XML IntelliSense is not available.</span></span>  
  
 <span data-ttu-id="88cef-105">Projeye dahil bir XML şema tanımı (XSD) şemasında bir hata var.</span><span class="sxs-lookup"><span data-stu-id="88cef-105">There is an error in an XML Schema Definition (XSD) schema included in the project.</span></span> <span data-ttu-id="88cef-106">Varolan XSD şema çakışmalarını proje için ayarlanmış bir XSD şema (.xsd) dosyası eklediğinizde, bu hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="88cef-106">This error occurs when you add an XSD schema (.xsd) file that conflicts with the existing XSD schema set for the project.</span></span>  
  
 <span data-ttu-id="88cef-107">**Hata Kimliği:** BC36810</span><span class="sxs-lookup"><span data-stu-id="88cef-107">**Error ID:** BC36810</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="88cef-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="88cef-108">To correct this error</span></span>  
  
-   <span data-ttu-id="88cef-109">Uyarı çift **hata listesine** penceresi.</span><span class="sxs-lookup"><span data-stu-id="88cef-109">Double-click the warning in the **Errors List** window.</span></span> <span data-ttu-id="88cef-110">Visual Basic Uyarı kaynağı XSD dosyası konumu için yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="88cef-110">Visual Basic will take you to the location in the XSD file that is the source of the warning.</span></span> <span data-ttu-id="88cef-111">XSD şemasında hatayı düzeltin.</span><span class="sxs-lookup"><span data-stu-id="88cef-111">Correct the error in the XSD schema.</span></span>  
  
-   <span data-ttu-id="88cef-112">Tüm gerekli XSD şema (.xsd) dosyaları projeye dahil emin olun.</span><span class="sxs-lookup"><span data-stu-id="88cef-112">Ensure that all required XSD schema (.xsd) files are included in the project.</span></span> <span data-ttu-id="88cef-113">' İ tıklatmanız gerekir **tüm dosyaları göster** üzerinde **proje** , .xsd görmek için menü dosyaları **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="88cef-113">You may need to click **Show All Files** on the **Project** menu to see your .xsd files in **Solution Explorer**.</span></span> <span data-ttu-id="88cef-114">Bir .xsd dosyasını sağ tıklatın ve ardından **projeye dahil et** dosyayı projenize eklemek için.</span><span class="sxs-lookup"><span data-stu-id="88cef-114">Right-click an .xsd file and then click **Include In Project** to include the file in your project.</span></span>  
  
-   <span data-ttu-id="88cef-115">XML ve şema Sihirbazı kullanıyorsanız, aynı kaynaktan birden fazla kez şemaları Infer bu hata oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="88cef-115">If you are using the XML to Schema Wizard, this error can occur if you infer schemas more than one time from the same source.</span></span> <span data-ttu-id="88cef-116">Bu durumda, varolan XSD şema dosyaları projeden kaldırmak eklemek yeni bir XML Şeması öğe şablonu için ve XML şema Sihirbazı'na tüm geçerli XML kaynaklarıyla projeniz için belirtin.</span><span class="sxs-lookup"><span data-stu-id="88cef-116">In this case, you can remove the existing XSD schema files from the project, add a new XML to Schema item template, and then provide the XML to Schema Wizard with all the applicable XML sources for your project.</span></span>  
  
-   <span data-ttu-id="88cef-117">XSD şemasında yok hatası belirlenirse, XML derleyici ayrıntılı hata iletisi sağlamak için yeterli bilgiye sahip olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="88cef-117">If no error is identified in your XSD schema, the XML compiler may not have enough information to provide a detailed error message.</span></span> <span data-ttu-id="88cef-118">XML ad alanları .xsd dosyaları için Visual Studio'da ayarlayın XML şeması için tanımlanan XML ad alanları, proje eşlemesinde dahil olmak değilse daha ayrıntılı hata bilgileri almak mümkün olabilir.</span><span class="sxs-lookup"><span data-stu-id="88cef-118">You may be able to get more detailed error information if you ensure that the XML namespaces for the .xsd files included in your project match the XML namespaces identified for the XML Schema set in Visual Studio.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88cef-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="88cef-119">See Also</span></span>  
 [<span data-ttu-id="88cef-120">Hata Listesi penceresi</span><span class="sxs-lookup"><span data-stu-id="88cef-120">Error List Window</span></span>](/visualstudio/ide/reference/error-list-window)  
 [<span data-ttu-id="88cef-121">XML</span><span class="sxs-lookup"><span data-stu-id="88cef-121">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
