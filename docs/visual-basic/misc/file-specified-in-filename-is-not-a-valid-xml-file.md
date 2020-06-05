---
title: Dosya adında belirtilen dosya geçerli bir XML dosyası değil
ms.date: 07/20/2015
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
ms.openlocfilehash: a84042490935e3e7e5a6de2a802d9effd5b4d3d4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84358354"
---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a><span data-ttu-id="18a07-102">Dosya adında belirtilen dosya geçerli bir XML dosyası değil</span><span class="sxs-lookup"><span data-stu-id="18a07-102">File specified in FileName is not a valid XML file</span></span>

<span data-ttu-id="18a07-103">Sağladığınız dosya adı geçerli bir XML dosyası değil.</span><span class="sxs-lookup"><span data-stu-id="18a07-103">The file name that you supplied is not a valid XML file.</span></span> <span data-ttu-id="18a07-104">Bir XML belgesinin izin verilen yapısını ve içeriğini belirtmek için bir belge türü tanımı (DTD), Microsoft XML verileri azaltılmış (XDR) şeması veya bir XML şeması tanım dili (XSD) şeması kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="18a07-104">To specify the allowed structure and content of an XML document, you can use a Document Type Definition (DTD), a Microsoft XML-Data Reduced (XDR) schema, or an XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="18a07-105">XSD şemaları, .NET Framework XML dilbilgisi belirtmek için tercih edilen yoldur.</span><span class="sxs-lookup"><span data-stu-id="18a07-105">XSD schemas are the preferred way to specify XML grammars in the .NET Framework.</span></span>

> [!NOTE]
> <span data-ttu-id="18a07-106">Visual Studio 'nun bazı önceki sürümlerinde **XML Designer** , türü belirtilmiş veri KÜMELERI ve XML şeması için tasarımcı olur.</span><span class="sxs-lookup"><span data-stu-id="18a07-106">In some earlier versions of Visual Studio, the **XML Designer** is the designer for typed datasets and XML schema.</span></span> <span data-ttu-id="18a07-107">XML **Designer** , XML şema dosyalarını oluşturmak ve düzenlemek için hala kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="18a07-107">The **XML Designer** can still be used to create and edit XML schema files.</span></span> <span data-ttu-id="18a07-108">Ancak, Visual Studio 2012 ' de, yazılan veri kümelerini oluşturma ve düzenlemeyle ilgili tasarımcı **veri kümesi Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="18a07-108">However, in Visual Studio 2012, the designer for creating and editing typed datasets is the **Dataset Designer**.</span></span> <span data-ttu-id="18a07-109">Daha fazla bilgi için bkz. [türü belirtilmiş veri kümeleri oluşturma ve düzenlemeyle](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/314t4see(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="18a07-109">For more information, see [Creating and Editing Typed Datasets](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/314t4see(v=vs.120)).</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="18a07-110">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="18a07-110">To correct this error</span></span>

- <span data-ttu-id="18a07-111">Doğru dosya adını tedarik edin.</span><span class="sxs-lookup"><span data-stu-id="18a07-111">Check that you are supplying the correct file name.</span></span>

- <span data-ttu-id="18a07-112">**XML tasarımcısına**denetlemek istediğiniz XML dosyasını yükleyerek, belirtilen DOSYANıN geçerli XML içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="18a07-112">Check that the specified file contains valid XML by loading the XML file that you want to check into the **XML Designer**.</span></span> <span data-ttu-id="18a07-113">**XML** menüsünde **XML 'yi doğrula**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="18a07-113">From the **XML** menu, click **Validate XML**.</span></span> <span data-ttu-id="18a07-114">Hatalar **görev listesi**görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="18a07-114">Errors are displayed in the **Task List**.</span></span>

- <span data-ttu-id="18a07-115">XML dosyasında ilişkili bir XML şeması varsa, öğelerin tanımlanan yapıda göründüğünden ve tek tek öğelerin içeriğinin şemada belirtilen tanımlanmış veri türlerine uygun olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="18a07-115">If the XML file has an associated XML Schema, check that the elements appear in the defined structure and that the content of the individual elements conforms to the declared data types specified in the schema.</span></span>

## <a name="see-also"></a><span data-ttu-id="18a07-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="18a07-116">See also</span></span>

- <xref:System.Xml>
- [<span data-ttu-id="18a07-117">Nasıl yapılır: Dosya Yollarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="18a07-117">How to: Parse File Paths</span></span>](../developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
