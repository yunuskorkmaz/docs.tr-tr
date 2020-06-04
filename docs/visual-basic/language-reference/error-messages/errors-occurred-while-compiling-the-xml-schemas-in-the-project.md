---
title: Projedeki XML şemaları derlenirken hataları oluştu
ms.date: 07/20/2015
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
ms.openlocfilehash: 919c6873ba63addb776d756a58c44a3fe3f0ec3d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409640"
---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a><span data-ttu-id="d7ea8-102">Projedeki XML şemaları derlenirken hataları oluştu</span><span class="sxs-lookup"><span data-stu-id="d7ea8-102">Errors occurred while compiling the XML schemas in the project</span></span>
<span data-ttu-id="d7ea8-103">Projedeki XML şemaları derlenirken hatalar oluştu.</span><span class="sxs-lookup"><span data-stu-id="d7ea8-103">Errors occurred while compiling the XML schemas in the project.</span></span> <span data-ttu-id="d7ea8-104">Bu nedenle, XML IntelliSense kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="d7ea8-104">Because of this, XML IntelliSense is not available.</span></span>  
  
 <span data-ttu-id="d7ea8-105">Projeye dahil edilen bir XML şema tanımı (XSD) şemasında bir hata var.</span><span class="sxs-lookup"><span data-stu-id="d7ea8-105">There is an error in an XML Schema Definition (XSD) schema included in the project.</span></span> <span data-ttu-id="d7ea8-106">Bu hata, proje için mevcut XSD şema kümesiyle çakışan bir XSD şeması (. xsd) dosyası eklediğinizde oluşur.</span><span class="sxs-lookup"><span data-stu-id="d7ea8-106">This error occurs when you add an XSD schema (.xsd) file that conflicts with the existing XSD schema set for the project.</span></span>  
  
 <span data-ttu-id="d7ea8-107">**Hata kimliği:** BC36810</span><span class="sxs-lookup"><span data-stu-id="d7ea8-107">**Error ID:** BC36810</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d7ea8-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="d7ea8-108">To correct this error</span></span>  
  
- <span data-ttu-id="d7ea8-109">**Hatalar Listesi** penceresinde uyarıya çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d7ea8-109">Double-click the warning in the **Errors List** window.</span></span> <span data-ttu-id="d7ea8-110">Visual Basic, sizi uyarının kaynağı olan XSD dosyasındaki konuma götürür.</span><span class="sxs-lookup"><span data-stu-id="d7ea8-110">Visual Basic will take you to the location in the XSD file that is the source of the warning.</span></span> <span data-ttu-id="d7ea8-111">XSD şemasında hatayı düzeltin.</span><span class="sxs-lookup"><span data-stu-id="d7ea8-111">Correct the error in the XSD schema.</span></span>  
  
- <span data-ttu-id="d7ea8-112">Tüm gerekli XSD şeması (. xsd) dosyalarının projeye eklendiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="d7ea8-112">Ensure that all required XSD schema (.xsd) files are included in the project.</span></span> <span data-ttu-id="d7ea8-113">. Xsd dosyalarınızı **Çözüm Gezgini**görmek için **Proje** menüsündeki **tüm dosyaları göster** ' e tıklamanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="d7ea8-113">You may need to click **Show All Files** on the **Project** menu to see your .xsd files in **Solution Explorer**.</span></span> <span data-ttu-id="d7ea8-114">Bir. xsd dosyasına sağ tıklayın ve dosyayı projenize dahil etmek için **projeye dahil et** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d7ea8-114">Right-click an .xsd file and then click **Include In Project** to include the file in your project.</span></span>  
  
- <span data-ttu-id="d7ea8-115">XML 'yi şema Sihirbazı ' nı kullanıyorsanız, şemaları aynı kaynaktan birden çok kez çıkarmanız durumunda bu hata ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="d7ea8-115">If you are using the XML to Schema Wizard, this error can occur if you infer schemas more than one time from the same source.</span></span> <span data-ttu-id="d7ea8-116">Bu durumda, var olan XSD şema dosyalarını projeden kaldırabilir, şema öğe şablonuna yeni bir XML ekleyebilir ve sonra projenize yönelik tüm geçerli XML kaynaklarıyla XML 'e şema Sihirbazı sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7ea8-116">In this case, you can remove the existing XSD schema files from the project, add a new XML to Schema item template, and then provide the XML to Schema Wizard with all the applicable XML sources for your project.</span></span>  
  
- <span data-ttu-id="d7ea8-117">XSD şemanızda herhangi bir hata tanımlanmamışsa, XML derleyicisi ayrıntılı bir hata iletisi sağlamak için yeterli bilgiye sahip olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="d7ea8-117">If no error is identified in your XSD schema, the XML compiler may not have enough information to provide a detailed error message.</span></span> <span data-ttu-id="d7ea8-118">Projenize dahil edilen. xsd dosyaları için XML ad alanlarının, Visual Studio 'da XML şeması kümesi için tanımlanan XML ad alanları ile eşleştiğinden emin olmanız durumunda daha ayrıntılı hata bilgileri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7ea8-118">You may be able to get more detailed error information if you ensure that the XML namespaces for the .xsd files included in your project match the XML namespaces identified for the XML Schema set in Visual Studio.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7ea8-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7ea8-119">See also</span></span>

- [<span data-ttu-id="d7ea8-120">Hata Listesi penceresi</span><span class="sxs-lookup"><span data-stu-id="d7ea8-120">Error List Window</span></span>](/visualstudio/ide/reference/error-list-window)
- [<span data-ttu-id="d7ea8-121">XML</span><span class="sxs-lookup"><span data-stu-id="d7ea8-121">XML</span></span>](../../programming-guide/language-features/xml/index.md)
