---
title: 'Öğretici: Regresyon kullanarak fiyatlarını tahmin etme'
description: Bu öğreticide, özellikle fiyatlarını tahmin etmek için New York City taksi fares ML.NET kullanarak bir regresyon modeli derler gösterilmektedir.
author: jralexander
ms.author: johalex
ms.date: 05/09/2019
ms.topic: tutorial
ms.custom: mvc, seodec18, title-hack-0516
ms.openlocfilehash: 40f70b6d89bf19ae0b20cb00d56e9f7dceb48f61
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66377788"
---
# <a name="tutorial-predict-prices-using-regression-with-mlnet"></a><span data-ttu-id="8ac0b-103">Öğretici: ML.NET ile regresyon kullanarak fiyatlarını tahmin etme</span><span class="sxs-lookup"><span data-stu-id="8ac0b-103">Tutorial: Predict prices using regression with ML.NET</span></span>

<span data-ttu-id="8ac0b-104">Bu öğreticide nasıl oluşturulacağını gösterir. bir [regresyon modeli](../resources/glossary.md#regression) Fiyatlar, özellikle tahmin etmek için New York City taksi fares ML.NET kullanma.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-104">This tutorial illustrates how to build a [regression model](../resources/glossary.md#regression) using ML.NET to predict prices, specifically, New York City taxi fares.</span></span>

<span data-ttu-id="8ac0b-105">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="8ac0b-106">Hazırlama ve verileri anlama</span><span class="sxs-lookup"><span data-stu-id="8ac0b-106">Prepare and understand the data</span></span>
> * <span data-ttu-id="8ac0b-107">Yükleme ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="8ac0b-107">Load and transform the data</span></span>
> * <span data-ttu-id="8ac0b-108">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="8ac0b-108">Choose a learning algorithm</span></span>
> * <span data-ttu-id="8ac0b-109">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="8ac0b-109">Train the model</span></span>
> * <span data-ttu-id="8ac0b-110">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="8ac0b-110">Evaluate the model</span></span>
> * <span data-ttu-id="8ac0b-111">Kullanım modeli tahminler elde etmek için</span><span class="sxs-lookup"><span data-stu-id="8ac0b-111">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8ac0b-112">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="8ac0b-112">Prerequisites</span></span>

* <span data-ttu-id="8ac0b-113">[Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-113">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="8ac0b-114">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="8ac0b-114">Create a console application</span></span>

1. <span data-ttu-id="8ac0b-115">Oluşturma bir **.NET Core konsol uygulaması** "TaxiFarePrediction" denir.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-115">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

1. <span data-ttu-id="8ac0b-116">Adlı bir dizin oluşturmak *veri* projenizdeki veri kümesi ve model dosyaları depolamak için.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-116">Create a directory named *Data* in your project to store the data set and model files.</span></span>

1. <span data-ttu-id="8ac0b-117">Yükleme **Microsoft.ML** NuGet paketi:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-117">Install the **Microsoft.ML** NuGet Package:</span></span>

    <span data-ttu-id="8ac0b-118">İçinde **Çözüm Gezgini**, projeye sağ tıklayıp seçin **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-118">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="8ac0b-119">Paket kaynağı, seçin "nuget.org" seçin **Gözat** sekmesinde, arama **Microsoft.ML**, listeden bir paket seçin ve seçin **yükleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-119">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the package in the list, and select the **Install** button.</span></span> <span data-ttu-id="8ac0b-120">Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-120">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="8ac0b-121">İçin de aynısını yapın **Microsoft.ML.FastTree** Nuget paketi.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-121">Do the same for the **Microsoft.ML.FastTree** Nuget package.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="8ac0b-122">Hazırlama ve verileri anlama</span><span class="sxs-lookup"><span data-stu-id="8ac0b-122">Prepare and understand the data</span></span>

1. <span data-ttu-id="8ac0b-123">İndirme [taksi taksi train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) ve [taksi taksi test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) veri ayarlar ve bunları kaydetmek *veri* önceki adımda oluşturduğunuz klasör.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-123">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="8ac0b-124">Machine learning modeli eğitmek ve modelin nasıl doğru olup'ı değerlendirmek için bu veri kümesi kullanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-124">We use these data sets to train the machine learning model and then evaluate how accurate the model is.</span></span> <span data-ttu-id="8ac0b-125">Bu veri kümesi başlangıçta arasındadır [NYC TLC taksi seyahat veri kümesi](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span><span class="sxs-lookup"><span data-stu-id="8ac0b-125">These data sets are originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

1. <span data-ttu-id="8ac0b-126">İçinde **Çözüm Gezgini**, her birini sağ tıklayın \*.csv dosyalarını ve select **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-126">In **Solution Explorer**, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="8ac0b-127">Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-127">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

1. <span data-ttu-id="8ac0b-128">Açık **taksi taksi train.csv** veri kümesi ve ilk satırında sütun üst bilgilerini bakın.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-128">Open the **taxi-fare-train.csv** data set and look at column headers in the first row.</span></span> <span data-ttu-id="8ac0b-129">Her sütun bir göz atın.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-129">Take a look at each of the columns.</span></span> <span data-ttu-id="8ac0b-130">Verileri anlamak ve hangi sütunların karar **özellikleri** hangisinin **etiket**.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-130">Understand the data and decide which columns are **features** and which one is the **label**.</span></span>

<span data-ttu-id="8ac0b-131">`label` Tahmin etmek istediğiniz sütun.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-131">The `label` is the column you want to predict.</span></span> <span data-ttu-id="8ac0b-132">Tanımlanan `Features`modeli tahmin etmek için size girişleri `Label`.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-132">The identified `Features`are the inputs you give the model to predict the `Label`.</span></span>

<span data-ttu-id="8ac0b-133">Sağlanan veri kümesi şu sütunları içerir:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-133">The provided data set contains the following columns:</span></span>

* <span data-ttu-id="8ac0b-134">**vendor_id:** Taksi satıcı kimliği bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-134">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="8ac0b-135">**rate_code:** Taksi dönüş oranı türünü bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-135">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="8ac0b-136">**passenger_count:** Bir özellik Yolcuların seyahat üzerinde sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-136">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="8ac0b-137">**trip_time_in_secs:** Seyahat geçen süre miktarı.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-137">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="8ac0b-138">Seyahat, taksi seyahat tamamlanmadan önce tahmin etmek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-138">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="8ac0b-139">Bu ne kadar seyahat bilmiyorum dakikamızı ayıralım.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-139">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="8ac0b-140">Bu nedenle, seyahat süresi, bir özellik değildir ve bu sütunu modelden dışında bırakacağız.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-140">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
* <span data-ttu-id="8ac0b-141">**trip_distance:** Seyahat mesafesini bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-141">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="8ac0b-142">**payment_type:** Ödeme yöntemini (nakit veya kredi kartı) bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-142">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="8ac0b-143">**fare_amount:** Ücretli toplam taksi taksi etiketi olur.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-143">**fare_amount:** The total taxi fare paid is the label.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="8ac0b-144">Veri sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="8ac0b-144">Create data classes</span></span>

<span data-ttu-id="8ac0b-145">Girdi verilerini ve Öngörüler için sınıflar oluşturun:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-145">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="8ac0b-146">İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-146">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="8ac0b-147">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *TaxiTrip.cs*.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-147">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="8ac0b-148">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-148">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="8ac0b-149">Aşağıdaki `using` yeni dosya için yönergeler:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-149">Add the following `using` directives to the new file:</span></span>

   [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="8ac0b-150">Varolan sınıf tanımına kaldırın ve iki sınıf olan aşağıdaki kodu ekleyin `TaxiTrip` ve `TaxiTripFarePrediction`, *TaxiTrip.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-150">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="8ac0b-151">`TaxiTrip` giriş verisi sınıfıdır ve her bir veri kümesi sütunları tanımlarına sahip.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-151">`TaxiTrip` is the input data class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="8ac0b-152">Kullanım <xref:Microsoft.ML.Data.LoadColumnAttribute> veri kümesinde kaynak sütunları dizin belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-152">Use the <xref:Microsoft.ML.Data.LoadColumnAttribute> attribute to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="8ac0b-153">`TaxiTripFarePrediction` Sınıfı, tahmini sonuçlar'ı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-153">The `TaxiTripFarePrediction` class represents predicted results.</span></span> <span data-ttu-id="8ac0b-154">Tek bir kayan noktalı sayı alana sahip `FareAmount`, ile bir `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> özniteliği uygulandı.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-154">It has a single float field, `FareAmount`, with a `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> attribute applied.</span></span> <span data-ttu-id="8ac0b-155">Regresyon görev durumunda **puanı** sütun tahmin edilen etiket değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-155">In case of the regression task the **Score** column contains predicted label values.</span></span>

> [!NOTE]
> <span data-ttu-id="8ac0b-156">Kullanım `float` giriş ve tahmin verilerini sınıflardaki kayan nokta değerlerini temsil eden tür.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-156">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

### <a name="define-data-and-model-paths"></a><span data-ttu-id="8ac0b-157">Veri ve model tanımlar</span><span class="sxs-lookup"><span data-stu-id="8ac0b-157">Define data and model paths</span></span>

<span data-ttu-id="8ac0b-158">Aşağıdaki ek ekleyin `using` üst tarafına deyimlerini *Program.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-158">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="8ac0b-159">Veri kümeleri dosyalarına ve modeli kaydedin ve dosyaya yolları tutmak için üç alanı oluşturmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-159">You need to create three fields to hold the paths to the files with data sets and the file to save the model:</span></span>

* <span data-ttu-id="8ac0b-160">`_trainDataPath` modeli eğitmek için kullanılan veri kümesiyle dosyasının yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-160">`_trainDataPath` contains the path to the file with the data set used to train the model.</span></span>
* <span data-ttu-id="8ac0b-161">`_testDataPath` model değerlendirmek için kullanılan veri kümesiyle dosyasının yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-161">`_testDataPath` contains the path to the file with the data set used to evaluate the model.</span></span>
* <span data-ttu-id="8ac0b-162">`_modelPath` eğitilen modelin depolandığı dosya yolu içerir.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-162">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="8ac0b-163">Aşağıdaki kod üzerinde doğru `Main` yöntemi bu yollarını belirtmek için ve `_textLoader` değişkeni:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-163">Add the following code right above the `Main` method to specify those paths and for the `_textLoader` variable:</span></span>

[!code-csharp[InitializePaths](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="8ac0b-164">Tüm ML.NET işlemleri başlangıç süresi [MLContext sınıfı](xref:Microsoft.ML.MLContext).</span><span class="sxs-lookup"><span data-stu-id="8ac0b-164">All ML.NET operations start in the [MLContext class](xref:Microsoft.ML.MLContext).</span></span> <span data-ttu-id="8ac0b-165">Başlatma `mlContext` modeli oluşturma iş akışı nesneleri arasında paylaşılabilir bir yeni ML.NET ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-165">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="8ac0b-166">Bu, kavramsal olarak, benzer `DBContext` Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-166">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="8ac0b-167">Ana değişkenleri başlatma</span><span class="sxs-lookup"><span data-stu-id="8ac0b-167">Initialize variables in Main</span></span>

<span data-ttu-id="8ac0b-168">Değiştirin `Console.WriteLine("Hello World!")` satırına `Main` bildirmek ve başlatmak için aşağıdaki kod ile yöntemi `mlContext` değişkeni:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-168">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create the ML Context")]

<span data-ttu-id="8ac0b-169">Sonraki kod satırı olarak ekleyin `Main` çağrılacak yöntem `Train` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-169">Add the following as the next line of code in the `Main` method to call the `Train` method:</span></span>

[!code-csharp[Train](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Train your model")]

<span data-ttu-id="8ac0b-170">`Train()` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-170">The `Train()` method executes the following tasks:</span></span>

* <span data-ttu-id="8ac0b-171">Verileri yükler.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-171">Loads the data.</span></span>
* <span data-ttu-id="8ac0b-172">Ayıklar ve verileri dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-172">Extracts and transforms the data.</span></span>
* <span data-ttu-id="8ac0b-173">Modeli eğitir.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-173">Trains the model.</span></span>
* <span data-ttu-id="8ac0b-174">Model döndürür.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-174">Returns the model.</span></span>

<span data-ttu-id="8ac0b-175">`Train` Yöntemi modeli eğitir.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-175">The `Train` method trains the model.</span></span> <span data-ttu-id="8ac0b-176">Bu yöntem oluşturma hemen altına `Main`, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-176">Create that method just below `Main`, using the following code:</span></span>

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

## <a name="load-and-transform-data"></a><span data-ttu-id="8ac0b-177">Veri yükleme ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="8ac0b-177">Load and transform data</span></span>

<span data-ttu-id="8ac0b-178">ML.NET kullanan [IDataView sınıfı](xref:Microsoft.ML.IDataView) sayısal ya da metin tablosal verileri açıklamak esnek ve verimli bir yolu olarak.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-178">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span></span> <span data-ttu-id="8ac0b-179">`IDataView` iki metin dosyalarını yükleyebilir veya gerçek zamanlı olarak (örneğin, SQL veritabanı veya günlük dosyaları).</span><span class="sxs-lookup"><span data-stu-id="8ac0b-179">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span></span> <span data-ttu-id="8ac0b-180">İlk satırı olarak aşağıdaki kodu ekleyin `Train()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-180">Add the following code as the first line of the `Train()` method:</span></span>

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "loading training dataset")]

<span data-ttu-id="8ac0b-181">Taksi seyahat taksi tahmin etmek istediğiniz gibi `FareAmount` sütun `Label` (modelin çıkış) tahmin kullanım `CopyColumnsEstimator` kopyalamak için dönüştürme sınıfına `FareAmount`ve aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-181">As you want to predict the taxi trip fare, the `FareAmount` column is the `Label` that you will predict (the output of the model)Use the `CopyColumnsEstimator` transformation class to copy `FareAmount`, and add the following code:</span></span> 

[!code-csharp[CopyColumnsEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Use the CopyColumnsEstimator")]

<span data-ttu-id="8ac0b-182">Modeli eğitir algoritması **sayısal** kategorik verileri dönüştürmek zorunda özellikleri (`VendorId`, `RateCode`, ve `PaymentType`) içine numaraları değerleri (`VendorIdEncoded`, `RateCodeEncoded`, ve `PaymentTypeEncoded`).</span><span class="sxs-lookup"><span data-stu-id="8ac0b-182">The algorithm that trains the model requires **numeric** features, so you have to transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) values into numbers (`VendorIdEncoded`, `RateCodeEncoded`, and `PaymentTypeEncoded`).</span></span> <span data-ttu-id="8ac0b-183">Bunu yapmak için kullanın [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) atayan farklı sayısal dönüştürme sınıfına anahtar sütunları farklı değerlerle değerlerini ve aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-183">To do that, use the [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) transformation class, which assigns different numeric key values to the different values in each of the columns, and add the following code:</span></span>

[!code-csharp[OneHotEncodingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Use the OneHotEncodingEstimator")]

<span data-ttu-id="8ac0b-184">Veri hazırlama son adımda tüm özellik sütunlara birleştirir **özellikleri** sütun kullanarak `mlContext.Transforms.Concatenate` dönüştürme sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-184">The last step in data preparation combines all of the feature columns into the **Features** column using the `mlContext.Transforms.Concatenate` transformation class.</span></span> <span data-ttu-id="8ac0b-185">Varsayılan olarak, bir öğrenme algoritması yalnızca özelliklerinden işler **özellikleri** sütun.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-185">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="8ac0b-186">Aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-186">Add the following code:</span></span>

[!code-csharp[ColumnConcatenatingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="8ac0b-187">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="8ac0b-187">Choose a learning algorithm</span></span>

<span data-ttu-id="8ac0b-188">Bu sorun, taksi seyahat taksi da oturan tahmin etme hakkında olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-188">This problem is about predicting a taxi trip fare in New York City.</span></span> <span data-ttu-id="8ac0b-189">İlk bakışta takip edilerek özgün uzaklık üzerinde yalnızca bağımlı görünüyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-189">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="8ac0b-190">Ancak, New York taksi satıcıları ek Yolcuların veya nakit yerine bir kredi kartıyla ödeme gibi diğer faktörlere için değişken miktarda ücret alınır.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-190">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span> <span data-ttu-id="8ac0b-191">Veri kümesindeki diğer etkenlere göre bir gerçek değer için fiyat değerini tahmin etmek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-191">You want to predict the price value, which is a real value, based on the other factors in the dataset.</span></span> <span data-ttu-id="8ac0b-192">Bunu yapmak için seçtiğiniz bir [regresyon](../resources/glossary.md#regression) machine learning görev.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-192">To do that, you choose a [regression](../resources/glossary.md#regression) machine learning task.</span></span>

<span data-ttu-id="8ac0b-193">Append [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) sonraki kod satırı olarak aşağıdakileri ekleyerek veri dönüştürme tanımlarını için machine learning görev `Train()`:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-193">Append the [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) machine learning task to the data transformation definitions by adding the following as the next line of code in `Train()`:</span></span>

[!code-csharp[FastTreeRegressionTrainer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="8ac0b-194">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="8ac0b-194">Train the model</span></span>

<span data-ttu-id="8ac0b-195">Eğitim modeline uygun `dataview` ve eğitim modeli, kod aşağıdaki satırı ekleyerek dönüş `Train()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-195">Fit the model to the training `dataview` and return the trained model by adding the following line of code in the `Train()` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#11 "Train the model")]

<span data-ttu-id="8ac0b-196">[Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) yöntemi, veri dönüştürme ve eğitim uygulayarak modelinizi eğitir.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-196">The [Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="8ac0b-197">Aşağıdaki kod satırı ile eğitilmiş modelin dönüş `Train()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-197">Return the trained model with the following line of code in the `Train()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="8ac0b-198">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="8ac0b-198">Evaluate the model</span></span>

<span data-ttu-id="8ac0b-199">Ardından, kalite güvencesi ve doğrulama test verilerinizle, model performansını değerlendirme.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-199">Next, evaluate your model performance with your test data for quality assurance and validation.</span></span> <span data-ttu-id="8ac0b-200">Oluşturma `Evaluate()` yöntemi hemen sonrasına `Train()`, aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-200">Create the `Evaluate()` method, just after `Train()`, with the following code:</span></span>

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="8ac0b-201">`Evaluate` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-201">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="8ac0b-202">Test veri kümesini yükler.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-202">Loads the test dataset.</span></span>
* <span data-ttu-id="8ac0b-203">Regresyon değerlendirici oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-203">Creates the regression evaluator.</span></span>
* <span data-ttu-id="8ac0b-204">Model değerlendirir ve ölçüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-204">Evaluates the model and creates metrics.</span></span>
* <span data-ttu-id="8ac0b-205">Ölçümleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-205">Displays the metrics.</span></span>

<span data-ttu-id="8ac0b-206">Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `Train` yöntemi çağrısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-206">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Call the Evaluate method")]

<span data-ttu-id="8ac0b-207">Test veri kümesini kullanarak yük [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-207">Load the test dataset using the [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method.</span></span> <span data-ttu-id="8ac0b-208">Bu veri kümesi kalite kontrolü kullanarak modeli değerlendirin aşağıdaki kodu ekleyerek `Evaluate` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-208">Evaluate the model using this dataset as a quality check by adding the following code in the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Load the test dataset")]

<span data-ttu-id="8ac0b-209">Ardından, dönüştürme `Test` aşağıdakileri ekleyerek veri kod için `EvaluateModel()`:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-209">Next, transform the `Test` data by adding the following code to `EvaluateModel()`:</span></span>

[!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Predict using the Transformer")]

<span data-ttu-id="8ac0b-210">[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemi giriş veri kümesi satırlarında test için Öngörüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-210">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for the test dataset input rows.</span></span>

<span data-ttu-id="8ac0b-211">`RegressionContext.Evaluate` Yöntemi hesaplar için Kalite Ölçümleri `PredictionModel` belirtilen veri kümesi kullanma.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-211">The `RegressionContext.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="8ac0b-212">Döndürür bir <xref:Microsoft.ML.Data.RegressionMetrics> regresyon değerlendiricisi tarafından hesaplanan toplam ölçümleri içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-212">It returns a <xref:Microsoft.ML.Data.RegressionMetrics> object that contains the overall metrics computed by regression evaluators.</span></span> 

<span data-ttu-id="8ac0b-213">Model kalitesini belirlemek için bunları görüntülemek için ölçümleri ilk almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-213">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="8ac0b-214">Sonraki satırda olarak aşağıdaki kodu ekleyin `Evaluate` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-214">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Compute Metrics")]

<span data-ttu-id="8ac0b-215">Ayarlanırsa, tahmin sonra [Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) yöntemi değerlendirir gerçek tahmin edilen değerlerle karşılaştırır modeli `Labels` modelin nasıl performans gösterdiğini üzerinde test veri kümesini ve döndürür ölçümleri de.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-215">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns metrics on how the model is performing.</span></span>

<span data-ttu-id="8ac0b-216">Modeli değerlendirme ve değerlendirme ölçümleri üretmek için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-216">Add the following code to evaluate the model and produce the evaluation metrics:</span></span>

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

<span data-ttu-id="8ac0b-217">[RSquared](../resources/glossary.md#coefficient-of-determination) regresyon modelleri, başka bir değerlendirme unsurdur.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-217">[RSquared](../resources/glossary.md#coefficient-of-determination) is another evaluation metric of the regression models.</span></span> <span data-ttu-id="8ac0b-218">RSquared 0 ile 1 arasındaki değerleri alır.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-218">RSquared takes values between 0 and 1.</span></span> <span data-ttu-id="8ac0b-219">Daha değerini 1 olarak daha iyi modelidir yakınız.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-219">The closer its value is to 1, the better the model is.</span></span> <span data-ttu-id="8ac0b-220">Aşağıdaki kodu ekleyin `Evaluate` yöntemi RSquared değerini görüntülemek için:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-220">Add the following code into the `Evaluate` method to display the RSquared value:</span></span>

[!code-csharp[DisplayRSquared](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#18 "Display the RSquared metric.")]

<span data-ttu-id="8ac0b-221">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) gerileme modelini değerlendirme ölçümlerini biridir.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-221">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) is one of the evaluation metrics of the regression model.</span></span> <span data-ttu-id="8ac0b-222">Daha düşük olan, daha iyi modelidir.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-222">The lower it is, the better the model is.</span></span> <span data-ttu-id="8ac0b-223">Aşağıdaki kodu ekleyin `Evaluate` yöntemi RMS değerini görüntülemek için:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-223">Add the following code into the `Evaluate` method to display the RMS value:</span></span>

[!code-csharp[DisplayRMS](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="8ac0b-224">Kullanım modeli tahminler elde etmek için</span><span class="sxs-lookup"><span data-stu-id="8ac0b-224">Use the model for predictions</span></span>

<span data-ttu-id="8ac0b-225">Oluşturma `TestSinglePrediction` yöntemi hemen sonrasına `Evaluate` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-225">Create the `TestSinglePrediction` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void TestSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="8ac0b-226">`TestSinglePrediction` Yöntemi aşağıdaki görevleri yürütür:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-226">The `TestSinglePrediction` method executes the following tasks:</span></span>

* <span data-ttu-id="8ac0b-227">Test verilerini tek bir yorum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-227">Creates a single comment of test data.</span></span>
* <span data-ttu-id="8ac0b-228">Test verilerini temel alarak taksi miktarı tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-228">Predicts fare amount based on test data.</span></span>
* <span data-ttu-id="8ac0b-229">Bir araya getirir, verileri ve raporlama için Öngörüler test edin.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-229">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="8ac0b-230">Tahmin edilen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-230">Displays the predicted results.</span></span>

<span data-ttu-id="8ac0b-231">Yeni yönteme bir çağrı ekleyin `Main` yöntemi, sağda altında `Evaluate` yöntemi çağrısı, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-231">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallTestSinglePrediction](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#20 "Call the TestSinglePrediction method")]

<span data-ttu-id="8ac0b-232">Kullanım `PredictionEngine` taksi aşağıdaki kodu ekleyerek tahmin etmek için `TestSinglePrediction()`:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-232">Use the `PredictionEngine` to predict the fare by adding the following code to `TestSinglePrediction()`:</span></span>

[!code-csharp[MakePredictionEngine](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#22 "Create the PredictionFunction")]

<span data-ttu-id="8ac0b-233">[PredictionEngine sınıfı](xref:Microsoft.ML.PredictionEngine%602) verileri tek bir örneğini geçirin ve sonra bir öngörü üzerinde gerçekleştirmek izin veren bir kolaylık API.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-233">The [PredictionEngine class](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass a single instance of data and then perform a prediction on it.</span></span>

<span data-ttu-id="8ac0b-234">Bu öğretici, bu sınıf içinde bir test seyahat kullanır.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-234">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="8ac0b-235">Daha sonra modeli denemek için diğer senaryolar ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-235">Later you can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="8ac0b-236">Eğitilen modelin Maliyet tahminini test etmek için bir seyahat ekleme `TestSinglePrediction()` bir örneğini oluşturarak yöntemi `TaxiTrip`:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-236">Add a trip to test the trained model's prediction of cost in the `TestSinglePrediction()` method by creating an instance of `TaxiTrip`:</span></span>

[!code-csharp[PredictionData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#23 "Create test data for single prediction")]

<span data-ttu-id="8ac0b-237">Ardından, taksi seyahat verilerini tek bir örneği temel taksi tahmin edin ve geçirin `PredictionEngine` aşağıdaki kodda bir sonraki satırı olarak ekleyerek `TestSinglePrediction()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-237">Next, predict the fare based on a single instance of the taxi trip data and pass it to the `PredictionEngine` by adding the following as the next lines of code in the `TestSinglePrediction()` method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#24 "Create a prediction of taxi fare")]

<span data-ttu-id="8ac0b-238">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi verileri tek bir örneği üzerinde bir tahmin sağlar.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-238">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single instance of data.</span></span>

<span data-ttu-id="8ac0b-239">Belirtilen seyahat, tahmin edilen taksi görüntülemek için aşağıdaki kodu ekleyin. `TestSinglePrediction` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-239">To display the predicted fare of the specified trip, add the following code into the `TestSinglePrediction` method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#25 "Display the prediction.")]

<span data-ttu-id="8ac0b-240">Test durumunuz için tahmin edilen taksi taksi görmek için programı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-240">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="8ac0b-241">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="8ac0b-241">Congratulations!</span></span> <span data-ttu-id="8ac0b-242">Başarıyla taksi seyahat fares tahmin etmeye yönelik bir machine learning modeli, doğruluğunun değerlendirilir, derleyip tahminlerde bulunmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-242">You've now successfully built a machine learning model for predicting taxi trip fares, evaluated its accuracy, and used it to make predictions.</span></span> <span data-ttu-id="8ac0b-243">Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub deposu.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-243">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8ac0b-244">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="8ac0b-244">Next steps</span></span>

<span data-ttu-id="8ac0b-245">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="8ac0b-245">In this tutorial, you learned how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="8ac0b-246">Hazırlama ve verileri anlama</span><span class="sxs-lookup"><span data-stu-id="8ac0b-246">Prepare and understand the data</span></span>
> * <span data-ttu-id="8ac0b-247">Öğrenme işlem hattı oluşturma</span><span class="sxs-lookup"><span data-stu-id="8ac0b-247">Create a learning pipeline</span></span>
> * <span data-ttu-id="8ac0b-248">Yükleme ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="8ac0b-248">Load and transform the data</span></span>
> * <span data-ttu-id="8ac0b-249">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="8ac0b-249">Choose a learning algorithm</span></span>
> * <span data-ttu-id="8ac0b-250">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="8ac0b-250">Train the model</span></span>
> * <span data-ttu-id="8ac0b-251">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="8ac0b-251">Evaluate the model</span></span>
> * <span data-ttu-id="8ac0b-252">Kullanım modeli tahminler elde etmek için</span><span class="sxs-lookup"><span data-stu-id="8ac0b-252">Use the model for predictions</span></span>

<span data-ttu-id="8ac0b-253">Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="8ac0b-253">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8ac0b-254">Iris kümelemesi</span><span class="sxs-lookup"><span data-stu-id="8ac0b-254">Iris clustering</span></span>](iris-clustering.md)
