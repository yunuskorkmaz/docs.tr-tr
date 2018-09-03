---
title: Dosya adında belirtilen dosya geçerli bir XML dosyası değil.
ms.date: 07/20/2015
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
ms.openlocfilehash: 3aecb0c2c87539717656a29f5b48f94fce3c8453
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43481882"
---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a><span data-ttu-id="338af-102">Dosya adında belirtilen dosya geçerli bir XML dosyası değil.</span><span class="sxs-lookup"><span data-stu-id="338af-102">File specified in FileName is not a valid XML file</span></span>
<span data-ttu-id="338af-103">Girdiğiniz dosya adı geçerli bir XML dosyası değil.</span><span class="sxs-lookup"><span data-stu-id="338af-103">The file name that you supplied is not a valid XML file.</span></span> <span data-ttu-id="338af-104">İzin verilen yapısı ve bir XML belgesinin içeriğini belirtmek için bir belge türü tanımı (DTD'nin), Microsoft XML verileri azaltılmış (XDR) şema veya bir XML Şeması Tanım Dili (XSD) şemaya kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="338af-104">To specify the allowed structure and content of an XML document, you can use a Document Type Definition (DTD), a Microsoft XML-Data Reduced (XDR) schema, or an XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="338af-105">XSD şemaları XML dilbilgisi sistemlerinde belirtmek için tercih edilen yolu olan [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="338af-105">XSD schemas are the preferred way to specify XML grammars in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="338af-106">Visual Studio'nun önceki bazı sürümlerinde **XML Tasarımcısı** türü belirtilmiş veri kümeleri ve XML şema Tasarımcısı.</span><span class="sxs-lookup"><span data-stu-id="338af-106">In some earlier versions of Visual Studio, the **XML Designer** is the designer for typed datasets and XML schema.</span></span> <span data-ttu-id="338af-107">**XML Tasarımcısı** XML şema dosyalarını oluşturmak ve düzenlemek için hala kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="338af-107">The **XML Designer** can still be used to create and edit XML schema files.</span></span> <span data-ttu-id="338af-108">Bununla birlikte, [!INCLUDE[vs_current_long](~/includes/vs-current-long-md.md)], oluşturma ve düzenleme türü belirtilmiş datasets için tasarımcı **veri kümesi Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="338af-108">However, in [!INCLUDE[vs_current_long](~/includes/vs-current-long-md.md)], the designer for creating and editing typed datasets is the **Dataset Designer**.</span></span> <span data-ttu-id="338af-109">Daha fazla bilgi için [oluşturma ve yazılan veri kümelerini düzenleme](/visualstudio/data-tools/creating-and-editing-typed-datasets).</span><span class="sxs-lookup"><span data-stu-id="338af-109">For more information, see [Creating and Editing Typed Datasets](/visualstudio/data-tools/creating-and-editing-typed-datasets).</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="338af-110">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="338af-110">To correct this error</span></span>  
  
-   <span data-ttu-id="338af-111">Doğru dosya adı sağlayarak denetleyin.</span><span class="sxs-lookup"><span data-stu-id="338af-111">Check that you are supplying the correct file name.</span></span>  
  
-   <span data-ttu-id="338af-112">Belirtilen dosya içine kontrol etmek istediğiniz XML dosyası yükleyerek geçerli XML içerdiğinden denetleyin **XML Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="338af-112">Check that the specified file contains valid XML by loading the XML file that you want to check into the **XML Designer**.</span></span> <span data-ttu-id="338af-113">Gelen **XML** menüsünü tıklatın **doğrulamak XML**.</span><span class="sxs-lookup"><span data-stu-id="338af-113">From the **XML** menu, click **Validate XML**.</span></span> <span data-ttu-id="338af-114">Hatalar görüntülenir **görev listesi**.</span><span class="sxs-lookup"><span data-stu-id="338af-114">Errors are displayed in the **Task List**.</span></span>  
  
-   <span data-ttu-id="338af-115">XML dosyası ilişkili bir XML şeması varsa, öğeleri tanımlanmış bir yapı içinde görünür ve tek tek öğelerine içeriğini belirtilen şemada bildirilen veri türleri için uygun olduğunu denetleyin.</span><span class="sxs-lookup"><span data-stu-id="338af-115">If the XML file has an associated XML Schema, check that the elements appear in the defined structure and that the content of the individual elements conforms to the declared data types specified in the schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="338af-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="338af-116">See Also</span></span>  
 <xref:System.Xml>  
 [<span data-ttu-id="338af-117">Nasıl Yapılır: Dosya Yollarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="338af-117">How to: Parse File Paths</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
