---
description: 'Hakkında daha fazla bilgi edinin: dosya adı içinde belirtilen dosya geçerli bir XML dosyası değil'
title: Dosya adında belirtilen dosya geçerli bir XML dosyası değil
ms.date: 07/20/2015
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
ms.openlocfilehash: c7d521986f3489345117a3947ed1e9b459af897e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472988"
---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a><span data-ttu-id="72d9f-103">Dosya adında belirtilen dosya geçerli bir XML dosyası değil</span><span class="sxs-lookup"><span data-stu-id="72d9f-103">File specified in FileName is not a valid XML file</span></span>

<span data-ttu-id="72d9f-104">Sağladığınız dosya adı geçerli bir XML dosyası değil.</span><span class="sxs-lookup"><span data-stu-id="72d9f-104">The file name that you supplied is not a valid XML file.</span></span> <span data-ttu-id="72d9f-105">Bir XML belgesinin izin verilen yapısını ve içeriğini belirtmek için bir belge türü tanımı (DTD), Microsoft XML-Data azaltılmış (XDR) şeması veya bir XML şeması tanım dili (XSD) şeması kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72d9f-105">To specify the allowed structure and content of an XML document, you can use a Document Type Definition (DTD), a Microsoft XML-Data Reduced (XDR) schema, or an XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="72d9f-106">XSD şemaları, .NET Framework XML dilbilgisi belirtmek için tercih edilen yoldur.</span><span class="sxs-lookup"><span data-stu-id="72d9f-106">XSD schemas are the preferred way to specify XML grammars in the .NET Framework.</span></span>

> [!NOTE]
> <span data-ttu-id="72d9f-107">Visual Studio 'nun bazı önceki sürümlerinde **XML Designer** , türü belirtilmiş veri KÜMELERI ve XML şeması için tasarımcı olur.</span><span class="sxs-lookup"><span data-stu-id="72d9f-107">In some earlier versions of Visual Studio, the **XML Designer** is the designer for typed datasets and XML schema.</span></span> <span data-ttu-id="72d9f-108">XML **Designer** , XML şema dosyalarını oluşturmak ve düzenlemek için hala kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="72d9f-108">The **XML Designer** can still be used to create and edit XML schema files.</span></span> <span data-ttu-id="72d9f-109">Ancak, Visual Studio 2012 ' de, yazılan veri kümelerini oluşturma ve düzenlemeyle ilgili tasarımcı **veri kümesi Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="72d9f-109">However, in Visual Studio 2012, the designer for creating and editing typed datasets is the **Dataset Designer**.</span></span> <span data-ttu-id="72d9f-110">Daha fazla bilgi için bkz. [türü belirtilmiş veri kümeleri oluşturma ve düzenlemeyle](/previous-versions/visualstudio/visual-studio-2013/314t4see(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="72d9f-110">For more information, see [Creating and Editing Typed Datasets](/previous-versions/visualstudio/visual-studio-2013/314t4see(v=vs.120)).</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="72d9f-111">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="72d9f-111">To correct this error</span></span>

- <span data-ttu-id="72d9f-112">Doğru dosya adını tedarik edin.</span><span class="sxs-lookup"><span data-stu-id="72d9f-112">Check that you are supplying the correct file name.</span></span>

- <span data-ttu-id="72d9f-113">**XML tasarımcısına** denetlemek istediğiniz XML dosyasını yükleyerek, belirtilen DOSYANıN geçerli XML içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="72d9f-113">Check that the specified file contains valid XML by loading the XML file that you want to check into the **XML Designer**.</span></span> <span data-ttu-id="72d9f-114">**XML** menüsünde **XML 'yi doğrula**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="72d9f-114">From the **XML** menu, click **Validate XML**.</span></span> <span data-ttu-id="72d9f-115">Hatalar **görev listesi** görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="72d9f-115">Errors are displayed in the **Task List**.</span></span>

- <span data-ttu-id="72d9f-116">XML dosyasında ilişkili bir XML şeması varsa, öğelerin tanımlanan yapıda göründüğünden ve tek tek öğelerin içeriğinin şemada belirtilen tanımlanmış veri türlerine uygun olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="72d9f-116">If the XML file has an associated XML Schema, check that the elements appear in the defined structure and that the content of the individual elements conforms to the declared data types specified in the schema.</span></span>

## <a name="see-also"></a><span data-ttu-id="72d9f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72d9f-117">See also</span></span>

- <xref:System.Xml>
- [<span data-ttu-id="72d9f-118">Nasıl yapılır: Dosya Yollarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="72d9f-118">How to: Parse File Paths</span></span>](../developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
