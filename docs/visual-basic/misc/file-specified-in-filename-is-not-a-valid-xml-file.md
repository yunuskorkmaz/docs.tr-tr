---
title: Dosya adında belirtilen dosya geçerli bir XML dosyası değil
ms.date: 07/20/2015
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
ms.openlocfilehash: 7d9500e58044f52a4e2508c9cb23a0e8186bc08d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553902"
---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a><span data-ttu-id="813f5-102">Dosya adında belirtilen dosya geçerli bir XML dosyası değil</span><span class="sxs-lookup"><span data-stu-id="813f5-102">File specified in FileName is not a valid XML file</span></span>

<span data-ttu-id="813f5-103">Sağladığınız dosya adı geçerli bir XML dosyası değil.</span><span class="sxs-lookup"><span data-stu-id="813f5-103">The file name that you supplied is not a valid XML file.</span></span> <span data-ttu-id="813f5-104">Bir XML belgesinin izin verilen yapısını ve içeriğini belirtmek için bir belge türü tanımı (DTD), Microsoft XML verileri azaltılmış (XDR) şeması veya bir XML şeması tanım dili (XSD) şeması kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="813f5-104">To specify the allowed structure and content of an XML document, you can use a Document Type Definition (DTD), a Microsoft XML-Data Reduced (XDR) schema, or an XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="813f5-105">XSD şemaları, .NET Framework XML dilbilgisi belirtmek için tercih edilen yoldur.</span><span class="sxs-lookup"><span data-stu-id="813f5-105">XSD schemas are the preferred way to specify XML grammars in the .NET Framework.</span></span>

> [!NOTE]
> <span data-ttu-id="813f5-106">Visual Studio 'nun bazı önceki sürümlerinde **XML Designer** , türü belirtilmiş veri KÜMELERI ve XML şeması için tasarımcı olur.</span><span class="sxs-lookup"><span data-stu-id="813f5-106">In some earlier versions of Visual Studio, the **XML Designer** is the designer for typed datasets and XML schema.</span></span> <span data-ttu-id="813f5-107">XML **Designer** , XML şema dosyalarını oluşturmak ve düzenlemek için hala kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="813f5-107">The **XML Designer** can still be used to create and edit XML schema files.</span></span> <span data-ttu-id="813f5-108">Ancak, Visual Studio 2012 ' de, yazılan veri kümelerini oluşturma ve düzenlemeyle ilgili tasarımcı **veri kümesi Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="813f5-108">However, in Visual Studio 2012, the designer for creating and editing typed datasets is the **Dataset Designer**.</span></span> <span data-ttu-id="813f5-109">Daha fazla bilgi için bkz. [türü belirtilmiş veri kümeleri oluşturma ve düzenlemeyle](/previous-versions/visualstudio/visual-studio-2013/314t4see(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="813f5-109">For more information, see [Creating and Editing Typed Datasets](/previous-versions/visualstudio/visual-studio-2013/314t4see(v=vs.120)).</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="813f5-110">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="813f5-110">To correct this error</span></span>

- <span data-ttu-id="813f5-111">Doğru dosya adını tedarik edin.</span><span class="sxs-lookup"><span data-stu-id="813f5-111">Check that you are supplying the correct file name.</span></span>

- <span data-ttu-id="813f5-112">**XML tasarımcısına**denetlemek istediğiniz XML dosyasını yükleyerek, belirtilen DOSYANıN geçerli XML içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="813f5-112">Check that the specified file contains valid XML by loading the XML file that you want to check into the **XML Designer**.</span></span> <span data-ttu-id="813f5-113">**XML** menüsünde **XML 'yi doğrula**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="813f5-113">From the **XML** menu, click **Validate XML**.</span></span> <span data-ttu-id="813f5-114">Hatalar **görev listesi**görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="813f5-114">Errors are displayed in the **Task List**.</span></span>

- <span data-ttu-id="813f5-115">XML dosyasında ilişkili bir XML şeması varsa, öğelerin tanımlanan yapıda göründüğünden ve tek tek öğelerin içeriğinin şemada belirtilen tanımlanmış veri türlerine uygun olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="813f5-115">If the XML file has an associated XML Schema, check that the elements appear in the defined structure and that the content of the individual elements conforms to the declared data types specified in the schema.</span></span>

## <a name="see-also"></a><span data-ttu-id="813f5-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="813f5-116">See also</span></span>

- <xref:System.Xml>
- [<span data-ttu-id="813f5-117">Nasıl yapılır: Dosya Yollarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="813f5-117">How to: Parse File Paths</span></span>](../developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
